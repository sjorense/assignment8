# FastAPI Calculator

This project is a small FastAPI web calculator that performs addition, subtraction, multiplication, and division. It includes a browser-based interface, API endpoints for each operation, automated tests, Docker support, and a GitHub Actions workflow that runs the test suite on every push to `main`.

## Features

- FastAPI application with HTML frontend
- Calculator operations for add, subtract, multiply, and divide
- Division-by-zero error handling
- Logging for successful operations and errors
- Unit tests for arithmetic functions
- Integration tests for API endpoints
- End-to-end tests with Playwright
- GitHub Actions CI workflow for automated testing
- Dockerfile and Docker Compose configuration

## Project Structure

```text
.
├── app/operations/__init__.py      # Calculator operation functions
├── main.py                         # FastAPI application and routes
├── templates/index.html            # Browser calculator interface
├── tests/unit/                     # Unit tests
├── tests/integration/              # API integration tests
├── tests/e2e/                      # Playwright end-to-end tests
├── .github/workflows/test.yml      # GitHub Actions test workflow
├── Dockerfile
├── docker-compose.yml
├── pytest.ini
└── requirements.txt
```

## Run Locally

Create and activate a virtual environment:

```bash
python3 -m venv venv
source venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
playwright install chromium
```

Start the application:

```bash
python main.py
```

Open the app in a browser:

```text
http://127.0.0.1:8000
```

## API Endpoints

Each endpoint accepts JSON with two numbers:

```json
{
  "a": 10,
  "b": 5
}
```

Available endpoints:

- `POST /add`
- `POST /subtract`
- `POST /multiply`
- `POST /divide`

Example response:

```json
{
  "result": 15
}
```

Division by zero returns an error response:

```json
{
  "error": "Cannot divide by zero!"
}
```

## Run Tests

Run the full test suite:

```bash
pytest -q
```

The suite includes:

- Unit tests for `add`, `subtract`, `multiply`, and `divide`
- Integration tests for all FastAPI calculator endpoints
- End-to-end Playwright tests that interact with the browser UI

## Docker

Build the Docker image:

```bash
docker build -t fastapi-calculator .
```

Run the container:

```bash
docker run --rm -p 8000:8000 fastapi-calculator
```

Or use Docker Compose:

```bash
docker compose up --build
```

## Continuous Integration

GitHub Actions is configured in `.github/workflows/test.yml`. On pushes and pull requests to `main`, the workflow:

1. Checks out the repository.
2. Sets up Python.
3. Installs dependencies and Playwright Chromium.
4. Runs the complete pytest suite.

## Repository

GitHub repository:

```text
https://github.com/sjorense/assignment8
```
