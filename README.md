# AWS CI/CD DEVOPS

This repository documents the design and implementation of a **CI/CD pipeline** for deploying a Java application using modern DevOps practices on AWS.  
The project highlights automation, scalability, and infrastructure management through industry-standard tools.

---

## 🎯 Project Overview

This project showcases:
- **Infrastructure as Code** using CloudFormation
- **Automated CI/CD Pipeline** with AWS CodePipeline and CodeBuild
- **Java Application Deployment** on EC2
- **GitHub Integration** for automated deployments on code push
- **Complete Free Tier Compliance** (no paid services used)

## 🏗️ Architecture

```
GitHub Repository
       ↓
AWS CodePipeline (triggered by Git push)
       ↓
AWS CodeBuild (compiles & packages Java app)
       ↓
AWS CloudFormation (provisions/updates infrastructure)
       ↓
Amazon EC2 t2.micro (runs Java web application)
       ↓
Amazon S3 (stores build artifacts)
```

## 📦 Technologies Used

- **Java 11** - Application runtime
- **Spring Boot** - Web framework
- **Maven** - Build tool
- **AWS CodePipeline** - CI/CD orchestration
- **AWS CodeBuild** - Build automation
- **AWS CloudFormation** - Infrastructure as Code
- **Amazon EC2 t2.micro** - Application server
- **Amazon S3** - Artifact storage
- **AWS IAM** - Access control
- **Amazon CloudWatch** - Monitoring and logs

## 🚀 Quick Start

### Prerequisites
- AWS Free Tier account 
- GitHub account
- Local machine with Git, Java 11+, and Maven

###  Instructions

1. Initialize the Repository  
Create a new repository on your GitHub account and set it up locally:
   ```

2. **Create AWS IAM Roles** (see Phase 1 documentation)
   - CodePipelineServiceRole
   - CodeBuildServiceRole
   - EC2InstanceRole

3. **Create EC2 Key Pair**
   ```bash
   # AWS Console → EC2 → Key Pairs → Create
   # Save as: aws-devops-key.pem
   chmod 600 ~/Downloads/aws-devops-key.pem
   ```

4. **Deploy CloudFormation Stack**
   ```bash
   aws cloudformation create-stack \
     --stack-name aws-devops-stack \
     --template-body file://infrastructure/infrastructure.yaml \
     --parameters ParameterKey=KeyPairName,ParameterValue=aws-devops-key \
     --region us-east-1
   ```

5. **Set up CodePipeline** (see Phase 5 documentation)
   - Connect GitHub repository
   - Configure CodeBuild project
   - Link CloudFormation deployment stage

6. **Push code to trigger pipeline**
   ```bash
   git add .
   git commit -m "Initial commit"
   git push origin main
   ```

## 📁 Project Structure

```
aws-free-tier-devops/
├── app/
│   ├── pom.xml                          # Maven configuration
│   └── src/
│       ├── main/
│       │   ├── java/com/awsdevops/
│       │   │   └── Application.java    # Spring Boot app
│       │   └── resources/
│       │       └── application.properties
│       └── test/
├── infrastructure/
│   └── infrastructure.yaml              # CloudFormation template
├── scripts/
│   └── deploy.sh                        # Deployment script
├── buildspec.yml                        # CodeBuild configuration
└── README.md                            # This file
```

## 🔗 Application Features

The deployed Java application displays:
- ✅ Deployment status badge
- 📅 Current timestamp of deployment
- 🖥️ EC2 instance details (hostname, IP, instance ID)
- 🛠️ Technology stack used
- 💰 "Deployed on AWS Free Tier" badge

```

## 📚 Learning Outcomes

This project demonstrates:
- ✅ Infrastructure as Code best practices
- ✅ CI/CD pipeline design and implementation
- ✅ AWS service integration and orchestration
- ✅ Security through IAM roles and least privilege
- ✅ Cost optimization (Free Tier usage)
- ✅ Application deployment automation