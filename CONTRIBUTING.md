## Contributing to Angular Console

We would love for you to contribute to Angular Console! Read this document to see how to do it.

## Got a Question?

We are trying to keep GitHub issues for bug reports and feature requests. Stack Overflow is a much better place to ask general questions about how to use Angular Console.

## Two Platforms

Angular Console runs on two platforms:

- Electron
- VSCode

The two versions of Angular Console share most of the code, but they are bundled differently. The dev experience is set up around the electron version.

## Development

After cloning the project run: `yarn`.

After that, run `nps prepare.electron`. Every time you add or remove dependencies in electron/package.json, you will need to rerun `nps prepare.electron`.

After this, run `nps dev.up` to start the dev environment. The application will start the process listening on port 4200. The development is done in the browser, but the server uses electron.

### Running Unit Tests

- Run `nps test` to run unit tests.

### Running E2e Tests

- Run `nps prepare.e2e` to build the project and create fixtures. This will create a few projects in the tmp folder you can develop against or run e2e tests against.
- Run `nps e2e.ci` to run e2e tests. This will compile and frontend and the backend, and run cypress tests (The fixtures must be created).
- Run `nps e2e.up` to serve the app and launch cypress. (The fixtures must be created). This is useful for development.
- Run `nps e2e.headless` to serve the app and run cypress from the terminal. (The fixtures must be created). This is also useful for development.

Cypress, which we use to run e2e tests, records the videos of the tests ran on CI. You can access them here: [https://dashboard.cypress.io/#/projects/x2ebye/runs](https://dashboard.cypress.io/#/projects/x2ebye/runs). This is very useful for troubleshooting.

## Building Electron App

You can build the electron app by running `nps package.electronMac` or `nps package.electronWin`. Usually, you only need to do it locally if you change something related to electron-builder.

## Building VSCode Plugin

You can build the vscode extension by running `nps prepare.and.package.vscode`.
You can install it by running `code --install-extension dist/apps/vscode/angular-console.vsix`
Reload the vscode window to use the newly installed build of the extension.

If you are working on the plugin, run:

- `nps build.dev.vscode` (This builds the client/server in watch mode)
- Wait for both client and server to be built.
- Hit F5

Now you can make changes to your code and the client/server builds will trigger.
When you want to see those reflected in VSCode, click the refresh button or hit F5 again.

## Submitting a PR

Please follow the following guidelines:

Run the following commands to make sure the linting and the tests pass.

- `nps format.check`
- `nps lint`
- `nps test`
- `nps e2e.prepare`
- `nps e2e.up`

If `nps format.check` fails, run `nps format`.

### Commit Message Guidelines

Commit message should follow the following format:

```
type: subject
BLANK LINE
body
```

#### Type

The type must be one of the following:

- build
- feat
- fix
- refactor
- style
- docs
- test

#### Subject

The subject must contain a description of the change.

#### Example

```
feat: add links to angular.io to the generate screen

The generate screen shows links to docs explaining all command-line options in depth
```
