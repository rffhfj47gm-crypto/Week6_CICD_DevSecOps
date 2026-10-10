# Week 6 CI/CD and DevSecOps sample
This is a demonstrator for Week 6 (Lab 2), not evidence of a completed GitHub Actions run.

## Local check
```bash
python -m pip install -r requirements-dev.txt
ruff check .
python -m pytest -q
bandit -r app.py -ll
pip-audit -r requirements.txt
docker build -t week6-app:local .
trivy image --severity HIGH,CRITICAL --exit-code 1 --ignore-unfixed week6-app:local
```
Push to a GitHub repository with `main` branch to run `.github/workflows/ci.yml`.
Save the successful/failed workflow page and Trivy step output as evidence for the lab.
A scan can fail because of newly disclosed CVEs; investigate rather than suppress findings.
