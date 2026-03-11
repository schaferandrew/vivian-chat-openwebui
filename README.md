# vivian-chat-openwebui

Open WebUI instance for Vivian — provides a chat UI connected to OpenRouter/Ollama models with MCP tool support via OpenAPI tool servers.

## Running

```bash
cp .env.example .env  # if .env doesn't exist yet
docker compose up -d
```

Open WebUI runs at **http://localhost:3060**.

## Connecting the MCP server

Open WebUI discovers tools via OpenAPI. Start `vivian-mcp-server` behind `mcpo` on the host:

```bash
# In vivian-mcp-server/
uvx mcpo --port 8001 -- uv run vivian-mcp
```

Then in Open WebUI: **Admin → Settings → Tools → Add Tool Server**

URL: `http://host.docker.internal:8001`

Save — all MCP tools are now available in chat.

## Environment variables

| Variable           | Description                                 |
|--------------------|---------------------------------------------|
| `WEBUI_SECRET_KEY` | Secret key for session signing              |
| `OLLAMA_BASE_URL`  | Ollama API URL (set to empty to disable)    |

See `.env.example` for the full list.
