# ☁️ AWS Secure 3-Tier Web Application Architecture

![AWS](https://img.shields.io/badge/AWS-Cloud-FF9900)
![EC2](https://img.shields.io/badge/Amazon%20EC2-Compute-orange)
![Aurora](https://img.shields.io/badge/Amazon%20Aurora-Database-blue)
![Route53](https://img.shields.io/badge/Route53-DNS-green)
![ACM](https://img.shields.io/badge/ACM-SSL%2FTLS-red)
![CloudWatch](https://img.shields.io/badge/CloudWatch-Monitoring-yellow)
![Secrets Manager](https://img.shields.io/badge/Secrets%20Manager-Security-purple)

---

## 📌 Overview

AWS Secure 3-Tier Web Application Architecture is a cloud-native deployment project that demonstrates the implementation of a scalable, secure, and highly available three-tier application on AWS.

The architecture separates the application into Frontend, Backend, and Database layers while integrating enterprise-grade AWS services such as Application Load Balancer (ALB), Route 53, AWS Certificate Manager (ACM), IAM Roles, Secrets Manager, Amazon Aurora, CloudWatch Monitoring, and SNS Alerting. The project follows security best practices by eliminating hardcoded credentials, enforcing HTTPS communication, and implementing infrastructure observability through centralized monitoring and alerts. :contentReference[oaicite:0]{index=0}

---

## ✨ Key Features

### 🌐 High Availability Architecture

- 3-Tier Application Design
- Application Load Balancer
- Route 53 DNS Routing
- Scalable EC2 Infrastructure
- Layered Architecture

### 🔒 Security & Compliance

- HTTPS Enforcement
- SSL/TLS Certificates using ACM
- IAM Role-Based Access
- Secrets Manager Integration
- Secure Database Connectivity

### ☁️ AWS Infrastructure

- Frontend EC2
- Backend EC2
- Amazon Aurora/MySQL
- Route 53
- Application Load Balancer

### 📊 Monitoring & Observability

- Amazon CloudWatch
- Resource Metrics Collection
- SNS Alert Notifications
- CPU Monitoring
- Memory Monitoring

### 🗄️ Database Layer

- Amazon Aurora
- MySQL-Compatible Database
- Persistent Data Storage
- User Authentication Data
- Student Registration Records

---

## 🏗️ System Architecture

```text

                                      Users
                                        │
                                        ▼

                                   Route 53
                                        │
                                        ▼

                         Application Load Balancer
                                        │
                  ┌─────────────────────┴─────────────────────┐
                  │                                           │
                  ▼                                           ▼

           Frontend Tier                               Backend Tier
        (Apache + HTML/JS)                         (Flask REST API)
                  │                                           │
                  │                                           ▼
                  │                                  Secrets Manager
                  │                                           │
                  └───────────────► Aurora MySQL ◄────────────┘
                                         │
                                         ▼

                                  CloudWatch Agent
                                         │
                                         ▼

                                     SNS Alerts

```

This architecture separates presentation, application, and database layers while integrating monitoring, security, and DNS services. :contentReference[oaicite:1]{index=1}

---

<details>
<summary><strong>⚙️ Tech Stack</strong></summary>

### ☁️ Cloud Platform

- AWS EC2
- Amazon Aurora
- Amazon RDS
- Route 53
- Application Load Balancer
- AWS IAM

### 🌐 Networking

- VPC
- Security Groups
- Route Tables
- DNS Routing
- Load Balancing

### 🔒 Security

- AWS Certificate Manager (ACM)
- AWS Secrets Manager
- IAM Roles
- HTTPS Encryption
- SSL/TLS Certificates

### 🖥️ Frontend

- HTML
- CSS
- JavaScript
- Apache Web Server

### ⚙️ Backend

- Python
- Flask
- Flask-CORS
- REST APIs
- MySQL Connector

### 📊 Monitoring

- Amazon CloudWatch
- CloudWatch Agent
- SNS Notifications

### 🗄️ Database

- Amazon Aurora
- MySQL

</details>

---

## 🔄 Application Workflow

```text
User Request → Route 53 DNS Resolution → Application Load Balancer → Frontend Application → Backend API → Amazon Aurora Database → Response to User
```

---

## 🌐 DNS & Load Balancing Workflow

```text
Custom Domain → Route 53 → Application Load Balancer → Frontend EC2 / Backend EC2
```

Route 53 provides DNS routing while ALB distributes traffic across application components. :contentReference[oaicite:2]{index=2}

---

## 🔒 HTTPS Architecture

The project secures application traffic using AWS Certificate Manager and Application Load Balancer HTTPS listeners.

### Security Features

- SSL/TLS Certificates
- HTTPS Listener Rules
- Automatic Certificate Validation
- Secure Traffic Encryption
- HTTP to HTTPS Redirection

### HTTPS Workflow

```text
Client Request → HTTPS (443) → ACM Certificate Validation → Application Load Balancer → Frontend / Backend Services
```

The implementation uses ACM-issued certificates integrated with ALB listeners for secure communication. :contentReference[oaicite:3]{index=3}

---

## 🔐 Secrets Management

AWS Secrets Manager is used to securely store database credentials instead of hardcoding them within application source code.

### Stored Secrets

- Database Username
- Database Password
- Database Endpoint
- Database Name

### Secret Retrieval Flow

```text
Backend EC2 → IAM Role Authentication → Secrets Manager → Database Credentials → Aurora Connection
```

This approach improves security and follows cloud security best practices. :contentReference[oaicite:4]{index=4}

---

## 📊 Monitoring & Alerting

CloudWatch provides centralized monitoring for backend infrastructure.

### Monitored Metrics

- CPU Utilization
- Memory Usage
- Resource Health
- Application Metrics

### Alert Workflow

```text
CloudWatch Metrics → Threshold Evaluation → SNS Topic → Email Notification
```

When CPU or memory thresholds exceed configured limits, SNS automatically sends notifications. :contentReference[oaicite:5]{index=5}

---

## 🗄️ Database Architecture

Amazon Aurora serves as the primary data layer for the application.

### Stored Data

- User Accounts
- Authentication Information
- Student Records
- Registration Data

### Database Workflow

```text
Frontend → Backend API → Aurora Database → Persistent Storage
```

Aurora provides managed relational database capabilities while supporting MySQL-compatible workloads. :contentReference[oaicite:6]{index=6}

---

## 🖼️ Project Preview

### 🔀 Flow Architecture

<p align="center">
  <img src="docs/3 Tier WebApp.png" width="90%">
</p>

---

<details>
<summary><strong>📁 Project Structure</strong></summary>

```text
aws-secure-3tier-webapp/
│
├── frontend/
│   ├── index.html
│   ├── backend.html
│   └── student.html
│
├── backend/
│   ├── app.py
│   ├── requirements.txt
│   └── database.py
│
├── database/
│   ├── schema.sql
│   └── setup.sql
│
├── architecture/
│   ├── route53-setup.md
│   ├── alb-configuration.md
│   ├── secrets-manager.md
│   └── cloudwatch-monitoring.md
│
├── docs/
│   ├── architecture.png
│   ├── cloudwatch.png
│   ├── route53.png
│   └── acm.png
│
└── README.md
```

</details>

---

## 🚀 Deployment Workflow

### Infrastructure Setup

- Create Security Groups
- Launch EC2 Instances
- Create Aurora Database
- Configure Networking

### Application Deployment

- Deploy Frontend Application
- Deploy Flask Backend
- Configure Database Connectivity

### Networking Configuration

- Create Target Groups
- Configure ALB
- Configure Route 53
- Register EC2 Targets

### Security Implementation

- Configure ACM Certificates
- Enable HTTPS
- Create IAM Roles
- Configure Secrets Manager

### Monitoring Setup

- Install CloudWatch Agent
- Configure Metrics Collection
- Create SNS Alerts
- Validate Monitoring

---

## 🛠️ Engineering Highlights

- 3-Tier Cloud Architecture
- Application Load Balancer Integration
- Route 53 DNS Routing
- HTTPS Enforcement using ACM
- IAM Role-Based Authentication
- AWS Secrets Manager Integration
- Amazon Aurora Deployment
- CloudWatch Monitoring
- SNS Alert Automation
- Secure Credential Management
- REST API Development with Flask
- Production-Ready Security Practices

---

## 🎯 Learning Outcomes

This project demonstrates practical experience with:

- AWS Cloud Architecture
- Application Load Balancers
- Route 53 DNS Management
- SSL/TLS Configuration
- IAM Role Management
- Secrets Management
- Amazon Aurora Administration
- CloudWatch Monitoring
- SNS Alerting Systems
- 3-Tier Application Design
- Secure Cloud Deployments
- Cloud Observability

---

## 🔮 Future Enhancements

### Scalability

- Auto Scaling Groups
- Multi-AZ Aurora
- Multi-Region Deployment
- Elastic Scaling

### Security

- AWS WAF
- AWS Shield
- Secrets Rotation
- Private Subnet Isolation

### Observability

- CloudWatch Dashboards
- AWS X-Ray
- Centralized Logging
- Performance Analytics

### Automation

- Terraform IaC
- Jenkins CI/CD
- GitHub Actions
- Automated Infrastructure Provisioning

---

## 📄 License

This project is intended for educational, learning, and portfolio demonstration purposes.

---

## 👨‍💻 Author

**Prabath D**
