# CloudTask

A simple Node.js task management API for demonstration and cloud deployment (Azure App Service).

**Project structure**
- `package.json` — project metadata and scripts.
- `server.js` — main Express server (API entrypoint).

**Features**
- RESTful API for tasks (CRUD).
- Lightweight single-file server suitable for quick deploys.
- Ready for deployment to Azure App Service.

## Prerequisites
- Node.js 18+ or a current LTS (Node 24+ recommended).
- npm (comes with Node.js) or Yarn.
- (Optional) Azure CLI for deployments.

## Installation
1. Clone the repository or copy the project files.
2. From the project root, install dependencies:

```bash
npm install
```

## Running locally
- Start with Node directly:

```bash
node server.js
```

- Or use npm script if defined:

```bash
npm start
```

The server typically listens on the port defined by the `PORT` environment variable (default `3000` if not set).

## Environment
- `PORT` — port the server listens on.
- Any other environment variables used by `server.js` should be documented in the file; add them here if your app requires them.

Set an environment variable and run locally (PowerShell example):

```powershell
$env:PORT=3000
node server.js
```

## API Endpoints (common)
Use these as a reference — confirm actual routes in `server.js`.

- `GET /api/tasks` — list all tasks
- `GET /api/tasks/:id` — get a single task by id
- `POST /api/tasks` — create a new task (JSON body)
- `PUT /api/tasks/:id` — update a task (JSON body)
- `DELETE /api/tasks/:id` — delete a task

Example: create a task with `curl`:

```bash
curl -X POST "http://localhost:3000/api/tasks" -H "Content-Type: application/json" -d '{"title":"Buy milk","done":false}'
```

## Deployment (Azure App Service quick guide)
1. Install and sign in to the Azure CLI: `az login`.
2. From project root, create a resource group (if needed):

```bash
az group create --name rg-cloudtask --location "EastUS"
```

3. Deploy using `az webapp up` (this will create an App Service and deploy):

```bash
az webapp up --name <your-app-name> --resource-group rg-cloudtask --runtime "NODE:24-lts"
```

Replace `<your-app-name>` with a globally unique name.

Notes: For advanced deployments, add a proper `start` script to `package.json` and include an `engines` field to pin the Node version.

## Testing
- There are no automated tests in this repository by default. Add a testing framework (Jest, Mocha) and test scripts in `package.json` as needed.

## Contributing
1. Fork the repo and create a feature branch.
2. Make changes and add tests where appropriate.
3. Open a pull request describing your changes.

## Troubleshooting
- If the server doesn't start, check `server.js` for required environment variables and ensure dependencies installed.
- For Azure deployment issues, inspect the App Service logs via the Azure portal or `az webapp log tail --name <your-app-name> --resource-group rg-cloudtask`.

## License
Specify a license for the project (e.g., MIT). If you don't have one yet, add a `LICENSE` file.

## Contact
For questions or help, open an issue in this repository or contact the maintainer.
