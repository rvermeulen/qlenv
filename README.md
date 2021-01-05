# Groom your CodeQL CLI environment with qlenv

Use qlenv to manage CodeQL CLI versions and allow per use case switching of versions.
Based on the awesome https://github.com/rbenv/rbenv and very much in alpha state.

The version to be used can be specified in the environment variable `CODEQL_VERSION` or in the file `.codeql-version`.
The environment variable overwrites possible version specifications in the `.codeql-version` file can exists anywhere on 
the path from the current working directory up to the root of the filesystem.

A default `~/.qlenv/version` file with the version specification can created to specify a defaul version if none is specified.

## Installation

**Note:** `qlenv` is currently only tested on MacOS Catalina and tries to support both MacOS and Linux at this point in time.

Clone the repository and ensure `~/.qlenv/bin` is on your `PATH`.

```bash
git clone git@github.com:rvermeulen/qlenv` ~/.qlenv
```

## Installing a CodeQL CLI

The `install` command relies on the [GitHub CLI](https://cli.github.com/) to be available on the `PATH`.

## Use with VS Code and the CodeQL extension

Unfortunately the invocation of `codeql` by the CodeQL extension doesn't provide means to locate the path to the folder that is opened by
VS Code so we can't use per project `.codeql-version` files.

To execute VS Code with a specific version you can install the `code` utility via the Command Pallet in VS Code using `Shell Command: Install 'code' command in PATH`.
Now by configuring the CodeQL extension to use the our shim by setting `codeQL.cli.executablePath` to `QLENV_LOCATION/bin/codeql` and executing `CODEQL_VERSION=x.y.z code PATH`
we can use version `x.y.z` in VS Code.
