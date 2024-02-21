# install-action

Github actions to install IaC vulnerability scanner.

## Learn More

- [About Accuknox](https://www.accuknox.com/)

## Inputs

```yamldsfan'
description: 'Run Scan against infrastructure as code.'
inputs:
  token:
    description: 'The token for authenticating with the CSPM panel.'
    required: true
  tenant_id:
    description: 'The ID of the tenant associated with the CSPM panel.'
    required: true
  endpoint:
    description: 'The URL of the CSPM panel to push the scan results to.'
    required: true
    default: 'cspm.demo.accuknox.com'
  github_pat:
    description: 'Environment variable name for a Github personal access token for scanning external modules sourced from private repositories'
    required: false
```

## Usage

Steps for using Install-action in a workflow yaml file 
- Checkout into the repo using checkout action.
- Utilize the accuknox/iac-scan-action repository with version tag v0.0.1.

### Token Generation from Accuknox SaaS and Viewing Tenant ID

Navigate to Tokens within the Settings section in the sidebar:
![1](https://github.com/udit-uniyal/container-scan-action/assets/115368361/8f4e188b-d9f3-4404-83af-134d5dc1417a)

Click on Create Token: 
After clicking on 'Create Token,' the Tenant ID will be visible.
![2](https://github.com/udit-uniyal/container-scan-action/assets/115368361/296bc611-acb8-4918-9d6b-3a8ec7733377)

Click on Generate:
![3](https://github.com/udit-uniyal/container-scan-action/assets/115368361/16032af0-bcac-4787-8f2a-a3fa0edc6ec6)


### workflow steps:

```yaml
      - name: Run IaC Scan
        uses: accuknox/iac-scan-action@v0.0.1
        with:      
          token: 
          endpoint: 
          tenant_id: 
```


## Minimalist Sample Configuration 

```yaml

name: AccuKnox Scan Workflow

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main

jobs:
  accuknox-cicd:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@main  
     
      - name: Run AccuKnox CSPM Scan
        uses: accuknox/iac-scan-action@v0.0.1
        with:
          token: 
          tenant_id:
          endpoint:
```
