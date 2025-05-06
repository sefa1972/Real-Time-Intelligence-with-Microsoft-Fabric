# Real Time Intelligence with Microsoft Fabric 

## Overview
This lab demonstrates how to use Microsoft Fabric's Real-Time Intelligence capabilities to ingest, analyze, and visualize real-time stock market data streams. You'll create an end-to-end solution including event streams, eventhouse storage, KQL queries, dashboards, and alerts.

## Prerequisites
- Microsoft Fabric tenant
- Web browser access

## Lab Steps

### 1. Create Workspace
1. Navigate to [Microsoft Fabric home page](https://app.fabric.microsoft.com)
2. Create new workspace with Fabric capacity

### 2. Set Up Real-Time Data Pipeline
1. **Create Eventstream**:
   - Connect to "Stock market sample" data source
   - Name eventstream `stock-data`

2. **Create Eventhouse**:
   - Create new Eventhouse resource
   - Set up KQL database with `stock` table
   - Connect eventstream to populate table

### 3. Query and Analyze Data

```kql

// View sample data

stock

| take 100

// Calculate 5-minute averages

stock

| where ["time"] > ago(5m)

| summarize avgPrice = avg(todecimal(bidPrice)) by symbol

| project symbol, avgPrice

```

### 4. Visualize Data
1. Create real-time dashboard
2. Pin query results as column chart
3. Customize visualization

### 5. Set Up Alerts
1. Configure price change alert:
   - Trigger when average price increases by 100
   - Group by stock symbol
   - Email notification action
2. Monitor alert history

## Key Learnings
- Real-time data ingestion with Eventstreams
- Time-series data storage in Eventhouse
- KQL query language for real-time analytics
- Live dashboard visualization
- Alert configuration with Activator

## Clean Up
1. Navigate to workspace settings
2. Select "Remove this workspace"

# 👤 Author >> Sefa Öztürk
IT Trainee | Azure Data Engineer in progress

📇 LinkedIn: https://www.linkedin.com/in/sefa-ozturk1972
