# Setup Poetry Action

[![version](https://img.shields.io/github/v/release/threeal/setup-poetry-action?style=flat-square)](https://github.com/threeal/setup-poetry-action/releases)
[![license](https://img.shields.io/github/license/threeal/setup-poetry-action?style=flat-square)](./LICENSE)
[![build status](https://img.shields.io/github/actions/workflow/status/threeal/setup-poetry-action/action.yaml?label=test&branch=main&style=flat-square)](https://github.com/threeal/setup-poetry-action/actions/workflows/action.yaml)

The Setup Poetry Action is a [GitHub Action](https://github.com/features/actions) designed to streamline the setup of [Poetry](https://python-poetry.org/), a powerful dependency and packaging manager for [Python](https://www.python.org/) projects. This action allows you to easily configure and use a specific version of Poetry within your GitHub Actions workflow, enabling you to build and test your Python project seamlessly.

## Usage

To get started with the Setup Poetry Action, you can refer to the [action.yaml](./action.yaml) file for detailed configuration options. Additionally, if you are new to GitHub Actions, you can explore the [GitHub Actions guide](https://docs.github.com/en/actions/learn-github-actions/understanding-github-actions) for a comprehensive overview.

### Inputs

Here are the available input parameters for the Setup Poetry Action:

| Name | Type | Default | Description |
| --- | --- | --- | --- |
| `version` | Version number or `latest` | `latest` | Specify the version of Poetry to be set up using this action. You can refer to the [Poetry release history](https://pypi.org/project/poetry/#history) for information about the available versions for setup. |
| `cache` | `true` or `false` | `true` | Indicates whether to use caching during Poetry installation. |

### Examples

Here is the basic example of how to use the Setup Poetry Action to set up Poetry for installing the dependencies of a Python project in your GitHub Actions workflow:

```yaml
name: Python CI
on:
  push:
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4.0.0

      - name: Setup Poetry
        uses: threeal/setup-poetry-action@main

      - name: Install Dependencies
        run: poetry install

      # Add more steps as needed for your workflow
```

#### Specifying Poetry Version

You can specify the Poetry version to be used by providing it as an input parameter:

```yaml
- name: Setup Poetry
  uses: threeal/setup-poetry-action@main
  with:
    version: 1.5.1
```

#### Combining with Setup Python Action

To set both the Python and Poetry versions, you can combine the Setup Poetry Action with the [Setup Python](https://github.com/actions/setup-python) action:

```yaml
- name: Setup Python
  uses: actions/setup-python@4.7.0
  with:
    python-version: 3.11

- name: Setup Poetry
  uses: threeal/setup-poetry-action@main
  with:
    version: 1.5.1
```

## License

This project is licensed under the terms of the [MIT License](./LICENSE).

Copyright © 2023 [Alfi Maulana](https://github.com/threeal/)
