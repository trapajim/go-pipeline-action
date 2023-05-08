# Go Pipeline

This is a composite Github Action to simplify the setup for Go projects.
Features of the action:
* setup go using `actions/setup-go@v4`
* run go test
* run go vet
* setup and run golangci-lint using `golangci/golangci-lint-action@v3`
* upload coverage to codecov


## Inputs

| Input Name | Description | Default Value |
| --- | --- | --- |
| go-version | The version of Go to use | stable |
| go-test-flags | Arguments for the `go test` command | `./... -v -covermode=atomic -coverprofile=coverprofile.out` |
| go-vet | A boolean flag indicating whether to run `go vet` | true |
| golangci-version | The version of the golangci-lint tool to use | latest |
| golangci-run | A boolean flag indicating whether to run golangci-lint | true |
| golangci-working-directory | The working directory for golangci-lint | ./ |
| golangci-args | The command line arguments for golangci-lint | `--issues-exit-code=0` |
| golangci-only-new-issues | A boolean flag indicating whether to show only new issues if it is a pull request | false |
| codecov-token | The token used to authorize coverage report uploads to Codecov, required if coverage should be uploaded to codecov | "" |
| coverage-file | The coverage file name | coverprofile.out |

## Example Usage

```yml

name: Go Pipeline

on: [push]

jobs:
  pipeline:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - uses: trapajim/go-pipeline-action@v1
        with:
          go-version: '1.20.1'
```
