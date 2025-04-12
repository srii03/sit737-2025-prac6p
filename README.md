# SIT737-2025-Prac6P: Kubernetes Deployment for Node.js Application

This repository contains the code and configuration for deploying a containerized Node.js application onto a Kubernetes cluster as part of the SIT737 Cloud Native Application Development course.

## Project Overview

In this project, a Node.js application is containerized using Docker, then deployed on a Kubernetes cluster to demonstrate the container orchestration process. The application runs in a Kubernetes environment and can be accessed through a NodePort service.

### Technologies Used:
- **Docker** for containerization
- **Kubernetes** for container orchestration
- **Node.js** for the backend application
- **kubectl** for managing the Kubernetes cluster
- **Git** for version control

## Prerequisites

Before you begin, ensure you have the following installed:

- [Docker](https://www.docker.com/products/docker-desktop)
- [Kubernetes](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [Minikube](https://minikube.sigs.k8s.io/docs/) (optional, for local Kubernetes setup)
- [Git](https://git-scm.com/)

## Setup Instructions

### 1. Clone the Repository

Start by cloning the repository to your local machine:


git clone https://github.com/your-username/sit737-2025-prac6p.git
cd sit737-2025-prac6p
2. Build the Docker Image
Build the Docker image for the Node.js application:


docker build -t sit737-node-app:latest .
3. Push Docker Image to Docker Hub
Push the Docker image to your Docker Hub repository:


docker tag sit737-node-app:latest your-dockerhub-username/sit737-node-app:latest
docker push your-dockerhub-username/sit737-node-app:latest
Replace your-dockerhub-username with your actual Docker Hub username.

4. Set Up Kubernetes Cluster (Optional)
If you're using Minikube locally, start your Minikube cluster:


minikube start
If you already have access to a Kubernetes cluster, ensure that kubectl is configured to point to that cluster.

5. Create Deployment and Service
Apply the Kubernetes Deployment and Service YAML files:


kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
This will create a Deployment for the Node.js application and a NodePort service to expose the application.

6. Verify the Deployment
Check the status of your pods and services:


kubectl get pods
kubectl get services
You should see your Node.js application running under the sit737-node-app Deployment, and the service should be accessible via the NodePort.

7. Access the Application
To access the deployed application, use the NodePort assigned to your service. You can find the NodePort by running:


kubectl get service sit737-node-app-service
Use the PORT and your Kubernetes node's external IP or localhost to access the application in your browser.

Example:

http://localhost:32039
8. Push Code to GitHub
If you have changes to push, follow these steps:

Add the changes:


git add .
Commit the changes:

git commit -m "Description of changes"
Push the changes to GitHub:


git push -u origin main
Files in this Repository
Dockerfile: Defines how to build the Node.js application Docker image.

deployment.yaml: Kubernetes Deployment configuration file for the Node.js application.

service.yaml: Kubernetes Service configuration file to expose the application via a NodePort.

server.js: The Node.js application source code.

Troubleshooting
If the application is not starting properly, check the logs using:


kubectl logs <pod-name>
If you encounter issues pulling the Docker image, ensure you are logged into Docker Hub using:

docker login
Conclusion
This project demonstrates how to deploy a containerized Node.js application on a Kubernetes cluster, making it scalable and easy to manage.

For more details, refer to the official Kubernetes Documentation.
