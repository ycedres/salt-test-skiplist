This repository contains a list of tests in the Salt Test Suite that are **not** executed.

The list is formatted using the TOML markup language. Skipped tests are grouped by file/test level and then by type. Missing groups do not have to be listed explicitly.

The list is used by [`salt-test`](https://github.com/openSUSE/salt-test#readme), a test launcher that skips the collection of files in the `[ignore]` sections and deselects all tests in the `[skip]` section.

### `ignore` vs `skip`

Prefer `skip` to `ignore`.
Reason: `ignore` skips over a whole Python module (i.e. a file). It's needed when the import of the module causes errors, e.g. `ImportError`. We don't have all of Salt's Python dependencies packaged and need to exclude files that don't guard their imports.
`skip` has finer granularity and is prefered for that reason.

### Adding new entries to `skipped_tests.toml`

This repository disallows direct commits to `main` to ensure all additions to `skipped_tests.toml` are agreed upon by [openSUSE's Salt team](https://github.com/orgs/openSUSE/teams/salt). All changes must come via a pull request that is approved by at least two other maintainers. All new entries must include a comment that explains why a given test is failing. The pull request description should explain why a test case is not getting fixed and instead added to this skiplist. Pull request reviewers are asked to critically review this explanation.