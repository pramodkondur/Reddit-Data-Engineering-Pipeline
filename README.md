# Data Engineering Pipeline Using Reddit, Airflow, Celery, PostgreSQL, S3, AWS Glue, Athena, and Redshift

This project provides a comprehensive data pipeline solution to extract, transform, and load (ETL) Reddit data into a Redshift data warehouse. The pipeline leverages a combination of tools and services, including Apache Airflow, Celery, PostgreSQL, Amazon S3, AWS Glue, Amazon Athena, and Amazon Redshift.

![img](images/reddit-hero.png)

Credits: [Reddit](www.reddit.com)

## Overview
The pipeline is designed to:

1. Extract data from Reddit using its API.
2. Store the raw data into an S3 bucket from Airflow.
3. Transform the data using AWS Glue and Amazon Athena.
4. Load the transformed data into Amazon Redshift for analytics and querying.

## Components Used:
1. **Reddit API**: Source of the data.
2. **Apache Airflow & Celery**: Orchestrates the ETL process and manages task distribution.
3. **PostgreSQL**: Temporary storage and metadata management.
4. **Amazon S3**: Raw data storage.
5. **AWS Glue**: Data cataloging and ETL jobs.
6. **Amazon Athena**: SQL-based data transformation.
7. **Amazon Redshift**: Data warehousing and analytics.

## Prerequisites
- AWS Account with appropriate permissions for S3, Glue, Athena, and Redshift.
- Reddit API credentials.
- Docker Installation
- Python 3.9 or higher

# Architecture
![img](images/Pipeline.png)

## Steps to Build the Data Pipeline

### 1. Set Up Docker
Docker is utilized in this project to create a consistent development environment. By using Docker, we can encapsulate all dependencies and services needed for the pipeline, ensuring that it runs the same way across different machines and environments.

#### Dockerfile and Docker Compose
Create a `Dockerfile` to define your application environment. Use `docker-compose.yml` to manage multi-container Docker applications.

### 2. Build the Docker Image
After setting up the `Dockerfile` and `docker-compose.yml`, build the Docker image using the following command:

### 3. Run Apache Airflow
Once the image is built, start the Apache Airflow web server and scheduler:

You can access the Airflow web interface at `http://localhost:8080`.

### 4. Create the Reddit ETL Pipeline
Next, write the ETL pipeline to fetch data from the Reddit API. This involves setting up a Directed Acyclic Graph (DAG) in Airflow for the Reddit extraction.

### 5. Store Data Locally
After extracting the data, you can save it locally in CSV format.

### 6. Set Up AWS S3
To store the CSV files, create an AWS IAM user and S3 bucket. Specify your AWS credentials in a configuration file so that Airflow can access them.

### 7. Create AWS Pipeline and ETL Jobs
Set up your AWS Glue jobs to perform ETL processes. This allows you to catalog and transform your data for analytics.

### 8. Use AWS Glue and Crawlers
AWS Glue provides a serverless ETL service. The Glue Crawlers can automatically detect and catalog the data from your S3 bucket. This allows you to run queries using Amazon Athena.

### 9. Query Data with Athena
Load your data into Athena, which allows you to run SQL queries on data stored in S3. This step is crucial for preparing data for further analysis.

### 10. Load Data into Amazon Redshift
After querying and transforming your data with Athena, load it into Amazon Redshift for high-performance analytics. Redshift allows for complex queries on large datasets.

### 11. Visualization
Finally, we can use tools like Power BI, Tableau, Looker, or Amazon QuickSight for further visualization and analysis of the data.

## Conclusion
This project demonstrates a complete data engineering pipeline using modern technologies. By integrating various services, we can efficiently manage the data flow from extraction to visualization, ensuring that insights can be derived from the Reddit data effectively.

## System Setup
1. Clone the repository.
   ```bash
    git clone https://github.com/pramodkondur/Reddit-Data-Engineering-Pipeline
   ```
2. Create a virtual environment.
   ```bash
    python3 -m venv venv
   ```
3. Activate the virtual environment.
   ```bash
    source venv/bin/activate
   ```
4. Install the dependencies.
   ```bash
    pip install -r requirements.txt
   ```
5. Rename the configuration file and the credentials to the file.
   ```bash
    mv config/config.conf.example config/config.conf
   ```
6. Starting the containers
   ```bash
    docker-compose up -d
   ```
7. Launch the Airflow web UI.
   ```bash
    open http://localhost:8080
   ```