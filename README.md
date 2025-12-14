# maven-build-action

GitHub action



## Usage

```yml
name: Build develop

on:
  push:
    branches:
      - main
  pull_request:
    branches:
      - main
  workflow_dispatch:

jobs:
  build:
    runs-on: ubuntu-latest

    permissions:
      contents: read
      packages: read

    steps:
      - uses: tiogars/maven-build-action@v1
        with:
          setup-java-server-username: ${{ github.actor }}
          setup-java-server-password: ${{ secrets.GITHUB_TOKEN }}
```

## Bump Patch Version

This repository includes a workflow to automatically bump the patch version of git tags. 

To bump the patch version:

1. Go to the **Actions** tab in the GitHub repository
2. Select the **Bump Patch Version** workflow
3. Click **Run workflow** button
4. The workflow will:
   - Find the latest semantic version tag (e.g., `v1.0.0`)
   - Increment the patch version (e.g., `v1.0.0` → `v1.0.1`)
   - Create and push the new tag to the repository

If no tags exist, it will create the first tag as `v0.0.1`.

**Note:** The workflow expects tags in the format `vMAJOR.MINOR.PATCH` (e.g., `v1.0.0`).
