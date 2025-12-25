# TIG Monitoring School Project (Telegraf / InfluxDB / Grafana)

## Objective

This project sets up a simple monitoring stack using **Telegraf**, **InfluxDB**, and **Grafana**.
It is intended for students to understand how basic system metrics can be collected, stored, and visualized using containers.

The monitored metrics include:
- CPU usage
- RAM usage

All components run using **Docker Compose**.

---

## Architecture Overview

The project uses three main services:

- **Telegraf**  
  Collects system metrics (CPU, memory, disk) from the environment where it runs.

- **InfluxDB**  
  Stores the metrics collected by Telegraf in a time-series database.

- **Grafana**  
  Displays the metrics using dashboards and graphs.


---

## Project Structure

```
docker_project_monitoring/
├── docker-compose.yml
├── telegraf.conf
├── grafana/
│   ├── dashboards/
│   └── provisioning/
└── README.md
```

---

## Docker Compose

The `docker-compose.yml` file starts the three services:
- InfluxDB on port `8086`
- Grafana on port `3001`, you can leave 3000 (mine was already taken)
- Telegraf as the metrics collector

Volumes are used to persist data for InfluxDB and Grafana.

---

## Telegraf Configuration

Telegraf is simply configured to collect:
- **CPU metrics** 
- **Memory metrics**

Metrics are collected every 10 seconds and sent to InfluxDB.

---

## InfluxDB

InfluxDB stores all metrics in a database named `telegraf`.

---

## Grafana

Grafana is used to visualize the metrics stored in InfluxDB.

Dashboards are:
- Created using the Grafana interface
- Automatically loaded at startup using provisioning files

Each dashboard shows:
- CPU usage in %
- RAM usage in % and in GB

---

## How to Run the Project

1. Start Docker Desktop
2. From the project directory, run:
   ```bash
   docker-compose up -d
   ```
3. Open Grafana in your browser:
   ```
   http://localhost:3001
   ```
4. Login with:
   - Username: `admin`
   - Password: `admin`

Dashboards should load automatically.

