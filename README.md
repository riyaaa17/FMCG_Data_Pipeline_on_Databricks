# FMCG_Data_Pipeline_on_Databricks
Absolutely! Below is a professional and well-structured **README.md** file for your GitHub repository. You can copy and paste it directly into your project.

---

# 📊 Atlon–Sports Bar Data Integration using Databricks Medallion Architecture

## 🚀 Project Overview

This project demonstrates the design and implementation of an end-to-end **Data Engineering Pipeline** using **Databricks Medallion Architecture**. It integrates structured enterprise data from Atlon with unstructured and inconsistent data from its acquired startup, Sports Bar, to create a unified analytics platform.

The solution transforms chaotic data into reliable, BI-ready insights, enabling consolidated dashboards for revenue analysis, supply chain forecasting, and inventory planning.

---

## 🏢 Business Scenario

**Atlon**, a leading sports equipment manufacturer, acquired **Sports Bar**, a fast-growing startup specializing in energy bars and athletic nutrition. While Atlon had a well-established data infrastructure, Sports Bar’s data was scattered across spreadsheets, cloud drives, WhatsApp exports, and ad-hoc APIs.

To enable unified analytics and reporting, a scalable Databricks pipeline was built to standardize and integrate data from both companies.

---

## 🎯 Project Objectives

* Build a reliable and scalable data pipeline for Sports Bar.
* Integrate Sports Bar’s data with Atlon’s existing Gold layer.
* Create a single source of truth for business intelligence.
* Enable unified dashboards for analytics and decision-making.
* Ensure scalability, reliability, and ease of maintenance.

---

## ✅ Success Criteria

* 📊 Reliable aggregated dashboards for both companies
* 📈 Scalable and future-ready architecture
* 👩‍💻 Low learning curve for new engineers
* 🔗 Seamless integration without disrupting Atlon’s systems

---

## 🏗️ Architecture Overview

### **Medallion Architecture**

The pipeline follows the Bronze, Silver, and Gold layering approach.

| Layer     | Description                  | Purpose                            |
| --------- | ---------------------------- | ---------------------------------- |
| 🥉 Bronze | Raw data ingestion           | Stores data in its original format |
| 🥈 Silver | Cleaned and transformed data | Standardizes and validates data    |
| 🥇 Gold   | BI-ready datasets            | Provides aggregated insights       |

### 🔄 Data Flow

```
Sports Bar OLTP CSVs → AWS S3 → Bronze → Silver → Gold
                                           ↓
                                   Merge with Atlon Gold
                                           ↓
                                   Unified Dashboards
```

---

## 📐 Data Model: Star Schema

### **Fact Table**

* **fact_orders**

  * order_date
  * customer_code
  * product_code
  * sold_quantity

### **Dimension Tables**

* **dim_customers**
* **dim_products**
* **dim_gross_price**
* **dim_date**

📌 **Revenue Formula:**

```
Revenue = Price × Quantity
```

---

## 📂 Repository Structure

```
📦 Atlon-SportsBar-Databricks-Project
│
├── 📁 data
│   ├── parent_company
│   │   ├── full_load
│   │   └── incremental_load
│   └── child_company
│       ├── full_load
│       └── incremental_load
│
├── 📁 notebooks
│   ├── 01_bronze_layer
│   ├── 02_silver_layer
│   ├── 03_gold_layer
│   ├── 04_fact_orders_full_load
│   ├── 05_fact_orders_incremental
│   └── 06_dim_date_generation
│
├── 📁 sql
│   └── sales_view.sql
│
├── 📁 dashboards
│   └── atlons_sales_insights.png
│
├── 📁 docs
│   └── architecture_diagram.png
│
├── README.md
└── requirements.txt
```

---

## ⚙️ Technology Stack

| Category          | Tools & Technologies         |
| ----------------- | ---------------------------- |
| Data Platform     | Databricks Community Edition |
| Processing Engine | Apache Spark                 |
| Programming       | PySpark, SQL                 |
| Storage           | AWS S3                       |
| Data Format       | Delta Lake                   |
| Data Modeling     | Star Schema                  |
| Orchestration     | Databricks Workflows         |
| Visualization     | Databricks Dashboards        |
| AI Assistant      | Databricks Genie             |

---

## 🔧 Implementation Details

### 🥉 Bronze Layer

* Ingests raw CSV files from AWS S3.
* Adds metadata such as `read_timestamp` and `file_name`.
* Stores data in Delta tables.

### 🥈 Silver Layer

* Cleans and standardizes data.
* Removes duplicates and trims spaces.
* Handles nulls and invalid values.
* Aligns schemas between Atlon and Sports Bar.

### 🥇 Gold Layer

* Creates BI-ready datasets.
* Performs aggregations and revenue calculations.
* Merges Sports Bar data with Atlon’s Gold layer.

---

## 🔄 Data Processing Strategy

### 📦 Historical Backfill

* Period: **July – November**
* Batch processing of legacy data.

### 📅 Incremental Processing

* Period: **December onwards**
* Daily ingestion using staging tables.

---

## 📊 Key Features

* ✔️ End-to-end ETL pipeline using Databricks
* ✔️ Medallion Architecture implementation
* ✔️ Delta Lake with ACID transactions and Time Travel
* ✔️ Star Schema for optimized analytics
* ✔️ Automated workflows with Databricks Jobs
* ✔️ Unified analytics across both companies
* ✔️ AI-powered insights using Databricks Genie

---

## 📈 Analytics and Dashboard

A denormalized view `gold.sales_view` was created for reporting and visualization.

### Key Insights:

* Total Revenue
* Sales Trends
* Top Products
* Customer Insights
* Channel Performance

---

## ▶️ Setup Instructions

### 1️⃣ Create Databricks Environment

```sql
CREATE CATALOG IF NOT EXISTS FMCG;
USE CATALOG FMCG;

CREATE SCHEMA IF NOT EXISTS bronze;
CREATE SCHEMA IF NOT EXISTS silver;
CREATE SCHEMA IF NOT EXISTS gold;
```

### 2️⃣ Upload Data

* Upload parent company data to the Gold layer.
* Upload Sports Bar data to AWS S3.

### 3️⃣ Run Notebooks in Sequence

1. Bronze Layer Notebooks
2. Silver Layer Notebooks
3. Gold Layer Notebooks
4. Fact Orders Full Load
5. Fact Orders Incremental Load
6. Sales View Creation

### 4️⃣ Create the Sales View

```sql
CREATE OR REPLACE VIEW FMCG.gold.sales_view AS
SELECT *
FROM FMCG.gold.fact_orders;
```


