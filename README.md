# Kairos – Scheduler & Publishing Agent

**Mission**: Schedule, post, and analyze content performance to optimize engagement timing.

## Core Capabilities

- Interface with LinkedIn API to publish approved posts
- Determine optimal timing windows based on engagement history
- Log publish metadata and retrieve analytics
- Feed performance data back into Mnemosyne

## API Endpoints

- `POST /v1/schedule` - Schedule content for publishing
- `POST /v1/publish` - Publish content immediately
- `GET /v1/posts/{id}` - Retrieve post status and analytics
- `GET /healthz` - Health check endpoint

## Key Deliverables

- `publish.json` schema for scheduled and published content
- LinkedIn API integration
- Timing optimization algorithms
- Analytics collection and reporting

## Dependencies

- Python 3.11+
- FastAPI, uvicorn
- LinkedIn API credentials
- Redis or Postgres for queue management
- Mnemosyne analytics interface

## Development

```bash
# Activate virtual environment
source .venv/bin/activate

# Run the service
uvicorn main:app --reload --port 8004

# Install additional dependencies
pip install <package>
pip freeze > requirements.txt
```

## Data Flow

Kairos receives cleaned content from Erebus and publishes to external platforms:

```
Erebus → Kairos → LinkedIn/External Platforms
           ↓
      Mnemosyne (performance tracking)
```

## Scheduling Intelligence

Kairos optimizes publishing through:
- **Historical engagement analysis**: Learn from past performance
- **Audience timing patterns**: Identify optimal posting windows
- **Content type correlation**: Match content types to timing
- **A/B timing tests**: Continuously refine scheduling

## Integration Points

- **n8n workflows**: Visual orchestration for approval flows
- **Notion approvals**: Human checkpoint before publication
- **LinkedIn API**: Primary publishing platform
- **Analytics feedback**: Performance data to Mnemosyne

## Related Repositories

- [agent-erebus](https://github.com/stephenpeters/agent-erebus) - Provides cleaned content
- [agent-mnemosyne](https://github.com/stephenpeters/agent-mnemosyne) - Receives performance data
- [agent-sdk](https://github.com/stephenpeters/agent-sdk) - Shared schemas and utilities
- [infra](https://github.com/stephenpeters/infra) - n8n workflow configuration
