# labpcf

A PowerApps Component Framework (PCF) project for building custom controls that can be used in Microsoft Dataverse / Power Apps model-driven and canvas apps.

## What's in here

### FirstControl

A minimal "hello world" style PCF **standard control** ([FirstControl/index.ts](FirstControl/index.ts)) that demonstrates the basic control lifecycle. On `init`, it creates a single `<input>` element with the text **"My First PCF"** and appends it to the container provided by the framework.

It exposes one bound property, `sampleProperty` (a `SingleLine.Text` field), declared in the control manifest ([FirstControl/ControlManifest.Input.xml](FirstControl/ControlManifest.Input.xml)), though the property isn't currently read or rendered by the control logic.

The control implements the standard PCF lifecycle methods:

| Method | Purpose |
| --- | --- |
| `init` | Initializes the control and renders the initial `<input>` element |
| `updateView` | Called whenever bound data or container properties change (currently a no-op) |
| `getOutputs` | Returns the control's output values back to the framework (currently empty) |
| `destroy` | Cleans up the control when it's removed from the DOM |

## Project structure

```
FirstControl/
  ControlManifest.Input.xml   # Control metadata: name, properties, resources
  index.ts                    # Control implementation
  generated/ManifestTypes.d.ts  # Auto-generated types from the manifest
labpcf.pcfproj                # PCF project file
pcfconfig.json                 # PCF build configuration
package.json                   # npm scripts and dependencies
```

## Prerequisites

- [Node.js](https://nodejs.org/) and npm
- [Power Platform CLI](https://learn.microsoft.com/power-platform/developer/cli/introduction) (`pac`)

## Getting started

Install dependencies:

```bash
npm install
```

Build the control:

```bash
npm run build
```

Run a local test harness in the browser (with hot reload):

```bash
npm run start:watch
```

Lint the code:

```bash
npm run lint
```

## Other available scripts

| Script | Description |
| --- | --- |
| `npm run clean` | Removes build output |
| `npm run rebuild` | Cleans and rebuilds the project |
| `npm run lint:fix` | Lints and automatically fixes issues |
| `npm run refreshTypes` | Regenerates `ManifestTypes.d.ts` from the manifest |
