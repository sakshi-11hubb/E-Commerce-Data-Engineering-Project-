# 📊 Multi-Source E-Commerce-Data-Engineering-Project

__📌 Overview__
---
This project demonstrates an end-to-end data engineering pipeline that integrates data from multiple sources and transforms it into a unified, analytics-ready dataset.

The pipeline ingests data from an SFTP server and an Azure SQL Database, processes and merges the data using PySpark in Azure Databricks, and loads the final dataset into Azure Data Lake Storage (ADLS) / Microsoft Fabric Lakehouse for reporting and analysis.

The solution focuses on data integration, transformation, and pipeline orchestration using industry-standard tools and best practices.

---
🎯 Project Objectives
---
* Integrate data from multiple sources (SFTP + Azure SQL)
* Perform data transformation and merging using PySpark
* Build a unified reporting dataset
* Automate data movement using Azure Data Factory (ADF)
* Store final data in ADLS / Fabric Lakehouse for analytics
---
🏗️ Architecture
---
**Data Flow:**

SFTP File + Azure SQL Database
→
Azure Data Factory (Ingestion & Orchestration)
→
ADLS (Raw / Bronze Layer)
→
Azure Databricks (PySpark Processing)
→
ADLS (Silver & Gold Layer)
→
ADF (Copy Activity)
→
Fabric Lakehouse / ADLS (Final Reporting Table)

---
🔄 Data Pipeline Workflow
--
1️⃣ Data Ingestion
- Extract data from:
  - SFTP server (CSV files) using WinSCP
  - Azure SQL Database (structured tables)
- SFTP Handling (WinSCP):
  - Connected to SFTP server using WinSCP
  - Downloaded raw CSV files from SFTP to local system
  - Uploaded files to Azure Data Lake Storage (ADLS - Bronze Layer)
- Azure SQL Data Ingestion:
  - Connected Azure SQL Database to Azure Data Factory (ADF)
  - Used ADF pipelines to extract and load data into ADLS
- Store all raw data in Bronze Layer (ADLS)

---
2️⃣ Data Transformation (PySpark)
---
- Load raw data into Azure Databricks
- Perform:
  - Data cleaning (null handling, duplicates removal)
  - Schema standardization
  - Data type conversion
- Merge datasets from SFTP and Azure SQL using joins
- Store processed data in Silver Layer (Delta format)

---
3️⃣ Data Aggregation (Gold Layer)
---
Create business-level metrics:
Total Sales
Revenue by State
Product Category Performance
Build final unified reporting table
Store in Gold Layer (Delta format)
