---
layout: post
title: Prediction of Remaining Useful Life (RUL) for Turbofan Engines
image: "/posts/Engine.jpg"
tags: [Predictive maintenance,RUL, Machine Learning, Python]
---
Our client, a grocery retailer, wants to utilise Machine Learning to reduce mailing costs, and improve ROI!

# Table of contents


- [00.Project Overview](#overview-main)
- [01.Dataset](#dataset)
- [02.CNN-SVR Model](#cnn-svr)
- [03.Web App](#web-app)
- [04.Deployment](#deployment)
  - [Local Deployment](#local-deployment)
  - [EC2 Deployment](#ec2-deployment)
- [05.Demo](#demo)

___

# Project Overview  <a name="overview-main"></a>



Accurately predicting a Turbofan engine's Remaining Useful Life (RUL) is crucial for effective maintenance planning and minimizing costly equipment downtime due to failures.This post contains code for predicting the RUL of a turbodan engine based on sensor data using a Convolutional Neural Network (CNN) and Support Vector Regression (SVR) model. It also includes a web app built using Streamlit for the front-end and FastAPI for the back-end. Docker is used to deploy the app on an EC2 instance.
<br>
<br>
__


# Dataset <a name="dataset"></a>

In this project, we utilized the NASA C-MAPSS Turbofan Engine Degradation Data Set, which is a simulated data set generated by the Commercial Modular Aero-Propulsion System Simulation (C-MAPSS) and available at [https://ti.arc.nasa.gov/c/6/](https://ti.arc.nasa.gov/c/6/). The data set is a multivariate time series that captures the operational cycles of specific engines identified by engine ID and cycle time. With multiple entries per engine at different reporting times, the data set includes diverse features, including 3 operational settings and 21 sensors. <br> 

<br>
<br>
___


# CNN-SVR Model <a name="cnn-svr"></a>

In this project, I propose a novel approach to predict RUL using a machine learning model that combines Convolutional Neural Networks (CNN) and Support Vector Regression (SVR) techniques.The proposed model consists of three convolutional layers, three max pooling layers, and a flattened layer in the CNN component, which extract essential features from the sensor data. These features are then used by the SVR component to predict the RUL.
<br>

![alt text](/img/posts/CNN_SVR.jpg "CNN_SVR")

<br>
<br>
___

# Web App <a name="web-app"></a>

To make this approach more accessible and user-friendly, I developed an app that allows users to upload a test data file, enter the engine number and current cycle, and receive a prediction of the RUL for their requested engine. The app uses Streamlit and FastAPI to facilitate seamless communication with the machine learning model, making it easier for users to obtain accurate RUL predictions for their Turbofan engines. 

<br>
<br>
___


# Deployment <a name="deployment-main"></a>
The app is deployed using Docker Compose on either a local machine or an EC2 instance. Docker Compose is used to start multiple Docker containers that make up the app. 

![alt text](/img/posts/Deployment_EC2.jpg "CNN_SVR")
<br>

## Local Deployment <a name="local-deployment"></a>
To deploy the app using Docker Compose on a local machine, follow these steps:

1. Clone the repo: `git clone https://github.com/safia-bashir/capstone_Project-Prediction-Of-Remaining-Useful-Life-of-Turbofan-Engine.git`
2. Install Docker and Docker Compose on your machine if they're not already installed: [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/) and [https://docs.docker.com/compose/install/](https://docs.docker.com/compose/install/)
3. Start the app using Docker Compose by running the following command in the same directory as your docker-compose.yml file: docker-compose up --build This will build the Docker images for the app and its dependencies, create and start the Docker containers, and expose the app on port 8501.
4. Open a web browser and go to http://localhost:8501 to use the app.
5. To stop the app and remove the Docker containers, run the following command: docker-compose down This will stop and remove the Docker containers created by the docker-compose up command.


## EC2 Deployment <a name="ec2-deployment"></a>

1. SSH into the EC2 instance.
2. Clone the repo: `git clone https://github.com/safia-bashir/capstone_Project-Prediction-Of-Remaining-Useful-Life-of-Turbofan-Engine.git`
3. Install Docker and Docker Compose on the EC2 instance if they're not already installed: [Docker Installation Guide](https://docs.docker.com/get-docker/) and [Docker Compose Installation Guide](https://docs.docker.com/compose/install/)
4. Start the app using Docker Compose by running the following command in the same directory as your docker-compose.yml file: `docker-compose up --build -d` This will build the Docker images for the app and its dependencies, create and start the Docker containers in detached mode, and expose the app on port 80.
5. To allow traffic to the app, configure the security group for the EC2 instance to allow inbound traffic on port 8000 and 8501.
6. Open a web browser and go to http://<ec2_instance_ip> to use the app.
7. To stop the app and remove the Docker containers, run the following command: `docker-compose down` This will stop and remove the Docker containers created by the docker-compose up command.

<br>
<br>
___



# Demo <a name="demo-main"></a>
[![Alt text](https://img.youtube.com/vi/05X7luF_MQc/0.jpg)](https://www.youtube.com/watch?v=05X7luF_MQc)