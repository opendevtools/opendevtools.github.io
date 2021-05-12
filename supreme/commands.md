# Commands

## add

### Git

Add a .gitignore with some common defaults.

```
supreme add git
```

### Husky

Install [`husky`](https://github.com/typicode/husky), a tool for git hooks, and setup
it up with [`pretty-quick`](https://github.com/azz/pretty-quick) that runs
`prettier` on staged files.

```
supreme add husky
```

### Jest

Install dependencies and configuration for Jest testing. It also adds scripts in package.json for running tests locally and in CI environments.

Installed npm dependencies: `jest`, `jest-watch-typeahead`, `is-ci-cli`

```
supreme add jest
```

### NVM

Add a .nvmrc with the current running Node version

```
supreme add nvm
```

### Prettier

Install `prettier` and add a `.prettierrc` with some defaults.

Installed npm dependencies: `prettier`

```
supreme add prettier
```

### Tailwind CSS

Install dependencies and configuration for Tailwind CSS

Installed npm dependencies: `tailwindcss`, `postcss`, `autoprefixer`

```
supreme add tailwind
```

## Config

### List

Display the current configuration

```
supreme config list
```

### Set

Update a configuration setting

- `--node` - Set if you want to use `npm` or `yarn` for installing Node
  dependencies [Possible values: `npm`, `yarn`]

```
supreme config set --node yarn
```

### Install

Install any Node package. Automatically selects `npm` or `yarn` depending on
which lockfile exists (or falls back to what's set in the config). If no arguments are passed it runs `npm install` or `yarn install`.

```
// Install all dependencies
supreme install

// Install one package
supreme install jest

// Install multiple
supreme install "jest prettier"

// Install with bash expansion
supreme install "jest prettier @types/{jest,react}"
```

## GitHub Actions

Create workflows for GitHub actions. It automatically detects these languages
and tweaks the config files:

- JavaScript / TypeScript
- ReScript
- Rust

### Files created

- `pr_check.yml` - Run tests and linting on pull requests targeting master branch
- `release.yml` - Run tests and publishes a new release on push to master branch

### Flags

- `--no-npm`, `-n` - Turn off `@semantic-release/npm` in `.releaserc` and remove `NPM_TOKEN` secret from `release.yml`
- `--project`, `-p` - Pass a supported project type [Possible values: `javascript`, `rescript`, `rust`]

### Environment variables

Environment variables are set inside GitHub repository settings -> Secrets.

- `GITHUB_TOKEN` - Added automatically by GitHub for each repo
- `NPM_TOKEN` (optional) - If you wish to publish the package/app to npm. If you don't want to build to npm then use the `--no-npm` flag.

```
supreme github-actions
```

## ReScript

Create a [ReScript](http://rescript-lang.org/) project with
[Tailwind](https://tailwindcss.com/).

```
supreme rescript my-project-name
```

You'll get some instructions after the project has been created

- `cd my-project-name`
- `npm install`
- `npm start` (start the compiler)
- `npm run server` (in another terminal window, start development server)

## GraphQL

Create a [GraphQL](https://graphql.org/) project.

```
supreme graphql my-project-name
```

You'll get some instructions after the project has been created

- `cd my-project-name`
- `npm install`
- `npm run dev` (start the development server)

### Run

List all available `package.json` `scripts`, select
one and `supreme` will run it.

```
supreme run
```

### Uninstall

Uninstall any Node package. Automatically selects `npm` or `yarn` depending on
which lockfile exists (or falls back to what's set in the config).

```
supreme uninstall
```

### Update dependencies

Update Node packages. Automatically selects `npm` or `yarn` depending on
which lockfile exists (or falls back to what's set in the config).

```
supreme update-dependencies
```
