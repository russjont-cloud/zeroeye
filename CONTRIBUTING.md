# Contributing

Thanks for helping improve this project. This guide covers the minimum setup and pull request workflow expected for contributions.

## Required Tools

Install the tools needed for the modules you plan to touch. The full repository build can check several language stacks:

- Python 3 with `python3` on your `PATH`
- Rust toolchain with `cargo`
- Node.js 22+ with `npm`
- Go with `go`
- C/C++ build tools: `gcc`, `g++`, `make`, and CMake 3.28+
- Java JDK 21 with `javac`
- Ruby with `ruby`
- Lua 5.4 with `luac`
- GHC and Cabal for Haskell/OpenAPI tooling

See the setup commands in [README.md](README.md#getting-started) for Ubuntu package examples.

## Local Setup

Fork and clone the repository:

```bash
git clone https://github.com/<your-username>/zeroeye.git
cd zeroeye
```

Install only the dependencies required for the area you are changing. For example:

```bash
# Python build tooling
python3 --version

# Frontend work
npm install

# Rust backend work
cargo fetch

# Go market module
go mod download
```

## Build and Diagnostics

Run the repository build before opening a pull request:

```bash
python3 build.py
```

The build writes diagnostic artifacts under `diagnostic/`. Include the generated files in your PR notes, especially:

- `diagnostic/build-<commit>.logd`
- `diagnostic/build-<commit>.json`

If the build fails because a language tool is missing, still include the diagnostic file names and summarize the failure. The diagnostics help reviewers reproduce your environment.

## Pull Request Workflow

1. Fork the repository.
2. Create a focused branch:

   ```bash
   git checkout -b fix/small-clear-description
   ```

3. Make one scoped change per PR.
4. Commit with a concise message:

   ```bash
   git commit -m "docs: add contribution guide"
   ```

5. Push your branch and open a pull request against `main`.
6. Use the [.github/pull_request_template.md](.github/pull_request_template.md) template.
7. In the PR description, include:
   - what changed,
   - how you tested it,
   - the `python3 build.py` result,
   - the generated diagnostic artifact names,
   - any limitations or missing local tools.

## Code Style

- Keep changes focused and avoid unrelated cleanup.
- Follow the style of the files you edit.
- Use readable names and small commits.
- Update documentation when behavior, setup, or configuration changes.
- This repository does not currently include an `.editorconfig`; if one is added later, follow it for whitespace and formatting rules.

## Before Submitting

- [ ] The change addresses one issue or purpose.
- [ ] `python3 build.py` was run.
- [ ] Diagnostic artifacts are mentioned in the PR notes.
- [ ] The PR uses `.github/pull_request_template.md`.
- [ ] No unrelated generated files are included, except required diagnostics.
