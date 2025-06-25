# JIRA Knowledge Pipeline

A daily automation pipeline that extracts closed JIRA tickets, processes summaries into contextual knowledge, and feeds into Ollama + LlamaAnything knowledge base.

## Overview

This project implements an automated pipeline that:
1. Extracts closed JIRA tickets on a daily basis
2. Processes ticket content into structured knowledge
3. Generates contextual summaries
4. Feeds processed data into Ollama + LlamaAnything knowledge base

## Architecture

The system uses a Docker Compose setup with three main components:

- **n8n**: Workflow automation engine that orchestrates the pipeline
- **Python JIRA Service**: Custom service for JIRA API integration and data processing
- **PostgreSQL**: Database for storing processed ticket data

## Prerequisites

- Docker and Docker Compose
- JIRA API access (API token)
- Ollama + LlamaAnything knowledge base setup

## Getting Started

1. Clone this repository
   ```bash
   git clone https://github.com/yourusername/jira-knowledge-pipeline.git
   cd jira-knowledge-pipeline
   ```

2. Configure environment variables
   ```bash
   cp .env.example .env
   # Edit .env with your JIRA API credentials
   ```

3. Start the services
   ```bash
   docker-compose up -d
   ```

4. Access n8n and import the workflow
   - Open http://localhost:5678 in your browser
   - Log in with the credentials from your .env file
   - Import the workflow from `n8n-workflows/jira-extraction-workflow.json`
   - Activate the workflow

## Project Structure

```
├── docker-compose.yml       # Docker Compose configuration
├── .env.example            # Environment variables template
├── jira-service/           # Python JIRA integration service
│   ├── Dockerfile          # Docker configuration for Python service
│   ├── requirements.txt    # Python dependencies
│   └── app.py             # Main Python application
├── n8n-workflows/         # n8n workflow definitions
│   └── jira-extraction-workflow.json  # Main workflow for JIRA extraction
└── PRD.md                 # Product Requirements Document
```

## Features

- Daily automated extraction of closed JIRA tickets
- Contextual summarization of ticket content
- Structured knowledge storage in PostgreSQL
- Integration with Ollama + LlamaAnything knowledge base
- Configurable workflow via n8n

## Development

### Extending the Python Service

To add new functionality to the Python service:

1. Modify `jira-service/app.py`
2. Rebuild the Docker image:
   ```bash
   docker-compose build jira-service
   docker-compose up -d jira-service
   ```

### Customizing n8n Workflows

1. Access the n8n web interface at http://localhost:5678
2. Modify the existing workflow or create new ones
3. Save and activate your changes

## Documentation

For detailed information about the project requirements and implementation, see the [PRD](./PRD.md).

## License

MIT