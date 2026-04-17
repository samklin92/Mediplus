
Author

OGAJI IGWE SAMUEL
Cloud & DevOps Engineer

GitHub: https://github.com/samklin92

LinkedIn: https://www.linkedin.com/in/igwe-ogaji

# 🏥 Medplus Cloud Deployment — Production DevOps Engineering Story

> Built and deployed a production-style medical application on AWS using Docker, CI/CD automation, and secure cloud architecture principles.

---

## 👨‍💻 Project Context

I joined **Medplus**, a medical technology company, as a DevOps Engineer and was tasked with taking a legacy application and transforming it into a **fully containerized, automated, and production-ready deployment on AWS**.

The goal was not just to deploy the application, but to design a system that is:

- Repeatable through automation
- Secure by default
- Scalable in cloud environments
- Easy to maintain using modern DevOps practices

This project reflects how I approach real-world DevOps work: **build once, automate everything, and remove manual deployment risk.**

---

## 🎯 What I Was Responsible For

I owned the end-to-end delivery of the deployment pipeline, including:

- AWS infrastructure setup for application hosting
- Containerization of the Medplus application using Docker
- Secure image storage using Amazon ECR
- Deployment orchestration on EC2 with Portainer
- CI/CD automation using GitHub Actions
- Reverse proxy configuration with Nginx / HAProxy
- SSL security implementation using Let’s Encrypt
- Domain routing and public application exposure

---

## 🏗️ System Architecture (How It Works)
Developer commits code
│
▼
GitHub Repository
│
▼
GitHub Actions CI/CD Pipeline
├── Build Docker Image
├── Run tests/validation
├── Push image to Amazon ECR
└── Trigger deployment on EC2
│
▼
AWS EC2 Instance (Ubuntu Server)
├── Docker Engine
├── Portainer (Container Management UI)
└── Medplus Application Container
│
▼
Reverse Proxy Layer (Nginx / HAProxy)
│
▼
SSL Encryption (Let’s Encrypt)
│
▼
Custom Domain (Route 53 / DNS Provider)

---

## 🛠️ Technology Stack

| Layer | Tools & Services |
|------|------------------|
| Cloud Platform | AWS (EC2, ECR, VPC, Security Groups) |
| Containerization | Docker |
| CI/CD Automation | GitHub Actions |
| Container Registry | Amazon ECR |
| Server Management | Portainer |
| Reverse Proxy | Nginx / HAProxy |
| SSL Security | Let’s Encrypt (Certbot) |
| Operating System | Linux (Ubuntu) |
| DNS | Route 53 / External DNS provider |

---

## 📦 Implementation Breakdown

### 1. Containerising the Application

The first step was to standardise the application environment using Docker.

- Created a Dockerfile for consistent builds
- Ensured environmental isolation
- Built a production-ready image

```bash
docker build -t medplus-app:v1.
2. Pushing Images to Amazon ECR

To securely store and version application images, I used Amazon ECR.

aws ecr get-login-password --region <region> | \
docker login --username AWS --password-stdin <account-id>.dkr.ecr.<region>.amazonaws.com

docker tag medplus-app:v1 <ecr-url>:v1
docker push <ecr-url>:v1

This created a secure, centralised container registry integrated with AWS IAM.

3. Deploying on EC2 with Portainer

I provisioned an Ubuntu EC2 instance and configured it as the runtime environment.

Inside the instance:

Installed Docker Engine
Installed Portainer for container management
Pulled images directly from ECR
Managed deployments via UI + automation

This allowed both manual visibility and automated deployment control.

4. CI/CD Automation with GitHub Actions

I implemented a fully automated delivery pipeline:

On every push to the main branch:

GitHub Actions builds the Docker image
Runs validation steps
Pushes image to Amazon ECR
Triggers deployment to EC2

This removed manual intervention from deployments completely.

5. Reverse Proxy + SSL Security Layer

To expose the application securely:

Configured Nginx / HAProxy as a reverse proxy
Routed traffic from the domain → application container
Enabled HTTPS using Let’s Encrypt SSL certificates
Forced secure encrypted traffic (HTTPS only)

This ensured production-grade security at the edge layer.

🔐 Security Implementation

Security was treated as a first-class concern:

All traffic is encrypted using HTTPS (TLS)
IAM-based access control for AWS resources
No hardcoded secrets (GitHub Secrets used instead)
Private container registry using Amazon ECR
Restricted EC2 inbound traffic via Security Groups
🌍 Final Deployment Outcome

Once completed, the system achieved:

Fully automated deployment pipeline (CI/CD)
Containerised application running on AWS EC2
Secure image management via ECR
Production-ready reverse proxy setup
HTTPS-secured public access via the domain
📈 Key Engineering Learnings

This project reinforced core DevOps principles:

Docker ensures consistency across environments
CI/CD pipelines eliminate manual deployment risk
Reverse proxies are critical for production traffic control
ECR integrates tightly with AWS IAM for secure image management
Automation improves reliability, speed, and confidence in deployments
👨‍💻 Author

OGAJI IGWE SAMUEL
Cloud & DevOps Engineer

GitHub: https://github.com/samklin92

LinkedIn: https://www.linkedin.com/in/igwe-ogaji
