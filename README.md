# HR-ASSIST: MCP-Powered HR Automation System

## Overview

HR-ASSIST is an Agentic AI system designed to automate routine HR workflows using the Model Context Protocol (MCP). The system enables HR teams to perform employee onboarding and related administrative tasks through natural language interactions.

The project uses Claude Desktop as the MCP client, while this repository contains the MCP server implementation along with custom HRMS tools responsible for employee management, ticket creation, meeting scheduling, leave management, and email notifications.

## Features

* Employee Onboarding Automation
* Employee Information Retrieval
* Leave Management
* Meeting Scheduling
* IT Asset & Support Ticket Creation
* Welcome Email Automation
* Natural Language Workflow Execution using MCP

## Tech Stack

* Python
* Model Context Protocol (MCP)
* Claude Desktop
* FastMCP
* UV Package Manager
* JSON Configuration
* Environment Variables

---

## Setup Instructions

### 1. Install Dependencies

```bash
uv init
uv add mcp[cli]
```

### 2. Configure Environment Variables

Create a `.env` file in the project root:

```env
CB_EMAIL=your_email@gmail.com
CB_EMAIL_PWD=your_gmail_app_password
```

### 3. Configure Claude Desktop

Add the following configuration to your Claude Desktop configuration file:

```json
{
  "mcpServers": {
    "hr-management-system": {
      "command": "C:\\Users\\YOUR_USERNAME\\.local\\bin\\uv.exe",
      "args": [
        "--directory",
        "C:\\path\\to\\hr-management-system",
        "run",
        "server.py"
      ],
      "env": {
        "CB_EMAIL": "your_email@gmail.com",
        "CB_EMAIL_PWD": "your_gmail_app_password"
      }
    }
  }
}
```

Replace the placeholder values with your local system paths and credentials.

### 4. Run the MCP Server

```bash
uv run server.py
```

### 5. Restart Claude Desktop

After starting the MCP server, restart Claude Desktop to load the custom HR tools.

---

## Example Prompt

```text
Onboard a new employee named Rahul Sharma who reports to Tony Sharma.
```

The agent will automatically:

* Add the employee to HRMS
* Create onboarding tickets
* Schedule an introductory meeting
* Send a welcome email
* Notify relevant stakeholders

---

## Project Architecture

```text
Claude Desktop
      │
      ▼
   MCP Client
      │
      ▼
 HR-ASSIST MCP Server
      │
      ├── Employee Management
      ├── Leave Management
      ├── Ticket Management
      ├── Meeting Scheduler
      └── Email Notifications
```

## Future Enhancements

* Remote MCP Deployment
* Web-Based Dashboard
* Multi-Agent HR Workflows
* Integration with Enterprise HRMS Platforms
* Role-Based Access Control
