### Flask-Azure-backend-example

This repository demonstrates how to build a Flask backend that integrates with **Azure Database for PostgreSQL**, utilizes **machine learning models**, and is **Dockerized** for portability and **deployed to Azure Kubernetes Service (AKS)** via **GitHub Actions**.

The project is intended as a **demo**, focusing on cloud integration and backend structure with a basic ML pipeline.

---

## Project Overview

- Flask API for training and prediction
- PostgreSQL database hosted on Azure
- Machine learning models trained using XGBoost and KMeans clustering
- Deployment automated using GitHub Actions
- Runs in a Docker container
- API routes include training, prediction, and test endpoints

---

## Features

### Flask Backend

- Modular Flask app under `apps/`
- CORS enabled for cross-origin requests
- API routes:
  - `/` – Health check
  - `/training` – Triggers the ML training pipeline
  - `/predict` – Accepts input and returns a predicted value
  - `/openai_service` – Placeholder for OpenAI integration

### Machine Learning Pipeline

- Training pipeline:
  - Fetches data from PostgreSQL
  - If data is missing, processes raw input and stores it in the database
  - Uses KMeans for clustering
  - Trains one XGBoost model per cluster
- Prediction pipeline:
  - Preprocesses input data
  - Identifies cluster via KMeans
  - Loads the respective model
  - Returns the predicted value

### Azure & DevOps

- **Database**: Azure Database for PostgreSQL
- **CI/CD**: GitHub Actions workflow in `.github/workflows/`
- **Deployment**: Azure Kubernetes Service (AKS)
- **Docker**: Containerization via `Dockerfile`
- **Secrets Management**: Environment variables through `.env` (excluded from Git)

---

# Install dependencies
pip install -r requirements.txt

# Run Flask app
python main.py

or using Docker 

docker build -t flask-azure-backend .
docker run -p 5000:5000 flask-azure-backend

# Dataset : https://www.kaggle.com/datasets/avikasliwal/used-cars-price-prediction/data?select=train-data.csv

