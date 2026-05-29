# IncidentPilot

**IncidentPilot** is an AI-powered incident response workflow simulator that demonstrates how modern operations teams can automate incident triage, investigation, remediation, and recovery workflows.

Built with **FastAPI**, IncidentPilot combines incident analysis, service observability, automated remediation, approval gates, and organizational memory into a single end-to-end workflow. The project simulates real-world incident management scenarios using production-like datasets and AI-driven decision-making.

---

## Overview

When an incident is reported, IncidentPilot:

1. Identifies the affected service and incident severity.
2. Analyzes historical incidents and successful fixes.
3. Collects logs, metrics, and service ownership information.
4. Generates a severity-aware response plan.
5. Executes remediation actions through simulated operational tools.
6. Enforces human approval for high-risk actions.
7. Verifies recovery and records successful resolutions for future incidents.

The platform demonstrates core concepts used in modern Site Reliability Engineering (SRE), DevOps, and AI Operations (AIOps) systems.

---

## Key Features

### AI-Driven Incident Triage

* Matches incoming incidents against a known incident catalog.
* Determines affected services and incident severity.
* Builds dynamic response plans based on incident context.

### Observability Integration

* Analyzes service logs.
* Evaluates operational metrics including:

  * CPU utilization
  * Memory utilization
  * P95 latency
  * Error rates
* Provides context-aware troubleshooting insights.

### Automated Remediation

* Executes simulated operational actions.
* Supports transient failure handling with automatic retries.
* Implements configurable restart strategies per service.

### Human-in-the-Loop Approval

* Requires manual approval before executing remediation actions for HIGH-severity incidents.
* Enables fully automated resolution paths for LOW-severity incidents.

### Organizational Memory

* Stores previously resolved incidents.
* Learns successful remediation strategies.
* Reuses historical knowledge to improve future workflows.

### Workflow Analytics

* Tracks execution progress in real time.
* Records latency for each workflow step.
* Calculates simulated operational cost per action.
* Maintains detailed execution logs.

---

## System Architecture

```text
                ┌─────────────────┐
                │   User Incident │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │ Incident Matcher│
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │ Response Planner│
                └────────┬────────┘
                         │
      ┌──────────────────┼──────────────────┐
      ▼                  ▼                  ▼
┌────────────┐    ┌────────────┐    ┌────────────┐
│ Log Reader │    │ Metrics    │    │ Service    │
│            │    │ Analyzer   │    │ Metadata   │
└────────────┘    └────────────┘    └────────────┘
      │                  │                  │
      └──────────────────┼──────────────────┘
                         ▼
                ┌─────────────────┐
                │ Remediation     │
                │ Engine          │
                └────────┬────────┘
                         │
            HIGH Severity Approval
                         │
                         ▼
                ┌─────────────────┐
                │ Recovery Verify │
                └────────┬────────┘
                         │
                         ▼
                ┌─────────────────┐
                │ Incident Memory │
                └─────────────────┘
```

---

## Technology Stack

### Backend

* FastAPI
* Python
* Uvicorn

### Data & Storage

* JSON-based incident datasets
* In-memory workflow state management
* Persistent incident memory store

### Observability Simulation

* Service logs
* Operational metrics
* Dependency mapping
* Service ownership metadata

### Workflow Engine

* Incident triage
* Response planning
* Approval gates
* Automated remediation
* Recovery verification

---

## Project Structure

```text
IncidentPilot/
│
├── data/
│   ├── incidents.json
│   ├── logs.json
│   ├── metrics.json
│   ├── services.json
│   └── memory.json
│
├── static/
├── templates/
├── main.py
├── requirements.txt
└── README.md
```

---

## Running Locally

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Start the Application

```bash
uvicorn main:app --reload
```

### Open the Dashboard

```text
http://127.0.0.1:8000
```

---

## Example Workflows

### High Severity Incident

Example:

```text
Payments API is slow
```

Workflow:

1. Incident identified and classified.
2. Logs and metrics analyzed.
3. Response plan generated.
4. Workflow pauses for human approval.
5. Service restart executed.
6. Recovery verified.
7. Incident memory updated.
8. Workflow marked as completed.

---

### Low Severity Incident

Example:

```text
Inventory sync lag is elevated for a subset of SKUs
```

Workflow:

1. Incident identified.
2. Observability signals analyzed.
3. Automated remediation executed.
4. Recovery verified.
5. Incident memory updated.
6. Workflow completed without approval.

---

## API Endpoints

| Method | Endpoint                               | Description                                 |
| ------ | -------------------------------------- | ------------------------------------------- |
| GET    | `/`                                    | Serves the frontend UI                      |
| GET    | `/api/incidents`                       | Returns available incidents                 |
| POST   | `/api/workflows`                       | Creates and starts a workflow               |
| GET    | `/api/workflows/{workflow_id}`         | Retrieves workflow state                    |
| POST   | `/api/workflows/{workflow_id}/approve` | Approves a high-severity remediation action |

---

## Learning Objectives

This project demonstrates:

* AI-assisted incident response workflows
* Human-in-the-loop automation
* Operational observability concepts
* Retry and failure recovery patterns
* Incident knowledge management
* Workflow orchestration
* AIOps-inspired system design
* SRE and DevOps incident handling practices

---

## Future Enhancements

* LLM-powered root cause analysis
* Vector-based incident memory search
* Slack and Microsoft Teams integrations
* PagerDuty integration
* Kubernetes remediation workflows
* Real-time streaming logs
* PostgreSQL persistence layer
* Multi-agent incident investigation system
* OpenTelemetry integration
* AI-generated postmortem reports

---

## Disclaimer

IncidentPilot is a demonstration project designed to showcase AI-assisted incident response workflows. All operational tools, remediation actions, notifications, and infrastructure interactions are simulated for educational and demonstration purposes.
