# AutoCodeRover GitHub Action

This GitHub Action runs [AutoCodeRover](https://github.com/nus-apr/auto-code-rover/), a tool for automatic program repair, on your repository.

## Inputs

### `bug_id`

**Required** The ID of the bug to repair.

## Example usage

```yaml
name: Run AutoCodeRover

on:
  workflow_dispatch:
    inputs:
      bug_id:
        description: 'Bug ID to repair'
        required: true
        type: string

jobs:
  repair:
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v2
    - name: Run AutoCodeRover
      uses: seekayel/auto-code-rover-action@v1
      with:
        bug_id: ${{ github.event.inputs.bug_id }}
```

## How it works

This action:

1. Sets up Python 3.8
2. Installs AutoCodeRover
3. Runs AutoCodeRover with the specified bug ID
4. Lists the repair results

## Outputs

The action will create a `repair_results` directory in your repository with the results of the repair attempt. You can access these results in subsequent steps of your workflow.

## Notes

- Make sure your repository is compatible with AutoCodeRover before using this action.
- The action uses Python 3.8. If you need a different version, you may need to modify the action.

## Contributing

Contributions to improve this action are welcome. Please feel free to submit a Pull Request.

## License

This GitHub Action is available under the [MIT License](LICENSE).