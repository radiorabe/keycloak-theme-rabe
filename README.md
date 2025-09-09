# RaBe Keycloak Theme

This repository contains our opinonated theme as well as some docs related to
the user experience of how we set up Keycloak at RaBe.

## Features

- RaBe look and feel
- Integration with our Mokey instance for password reset
- Updated translations properties to use wording familiar to our users

## Keycloak Support Matrix

Shows what version of Keycloak the theme is compatible with.

| Theme Version | 14.x | 15.x | 20.x | 26.x |
| ------------- | ---- | ---- | ---- | ---- |
| 0.1           | ✅   |      |      |      |
| 0.2           |      | ✅   |      |      |
| 0.3           |      |      | ✅   |      |
| 0.4           |      |      |      | ✅   |

### Language Support

We currently suppport the `de` and `en` locales of Keycloak. More locales might be added once our current strings are adapted and stable.

## Deployment

### Release

This project uses [jgitver](https://jgitver.github.io/) for managing its version.

To publish a new release, you have to create an annotated tag and push it:

```bash
VER=v0.0.0

git tag -a $VER

git push origin --tags
```

Once tagged, the ci pipeline should publish publish the jar to GitHub packages and also create a release.

### Build Archive

```
mvn package -f ./pom.xml
```

### Install Archive

To deploy the archive to Keycloak simply drop it into the standalone/deployments/ directory of Keycloak and it will be automatically loaded.

## The `rabe` Theme

### Login Theme

`src/main/resources/theme/rabe/login/login.ftl` is a copy of the base version with the small change of linking to our mokey instance for password reset.

`src/main/resources/theme/rabe/login/resources/css/style.css` updates css variables to replace colors and fonts.

### Account Console Theme

## Configuration

### Properties

Our theme uses the following properties:

| Property                | Description                                  |
| ----------------------- | -------------------------------------------- |
| `rabePasswordResetLink` | URL to our mokey instance for password reset |

### Auth Flows

We currently support a basic username/password form based flow and are preparing a WebAuthn passwordless flow to replace it.

## Known Issues

- [KEYCLOAK-18556](https://issues.redhat.com/browse/KEYCLOAK-18556): "Try another way to log in" does not work if the other way is a federated login.
- [KEYCLOAK-16075](https://issues.redhat.com/browse/KEYCLOAK-16075): Security key prompt is not show without user interaction

## Licence

This software is free software: you can redistribute it and/or modify it under the terms of the GNU Affero General Public License as published by the Free Software Foundation, version 3 of the License.

## Copyright

Copyright (c) 2021 [Radio Bern RaBe](https://rabe.ch)
