# Scoped packages
author: catalin

levels:

  - basic

  - advanced

  - medium

type: normal

category: feature

links:

  - '[docs.npmjs.com](https://docs.npmjs.com/misc/scope){website}'

  - >-
    [docs.npmjs.com](https://docs.npmjs.com/getting-started/scoped-packages){website}

---
## Content

Since `npm` started supporting scoping, multiple packages can have the same name while they are under a different **scope** (that acts like a namespace).

The naming convention for scopes is the same as with package names: **url-safe characters**, ** no leading dots or underscores**. Scopes are prefixed by `@`-symbol, followed by a `/` and will precede the package name:
```bash
@myscope/mypackagename
```

This syntax must be used when trying to `install` a package or specify a package in `package.json`:
```bash
$ npm intall @myscope/mypackagename
```
```json
//package.json
"dependencies: {
  "@myscope/mypackagename: "~1.3.3"
}
```

To initialise a scoped package, the scope must be specified in the package name:
```json
{ 
  "name": "@myscope/myprojectname"
}
```
`--scope` flag for `npm init` also works:
```bash
$ npm init -scope=myscope
```
Note that scoped packages are by default private so to publish a public one you must specify it:
```bash
$ npm publish --access=public
```
To use a scoped package you need to `require` it using the scoped name:
```js
var scopedPackage =
  require('@myscope/somePackage');

```