# OAuth2 as OpenAPI Spec 3.0 components

The example file which describes OAuth2 token endpoints located [dist/oauth2_endpoints.yml](dist/oauth2_endpoints.yml).

## Why this package exists
Since [RFC 6749 OAuth2](https://tools.ietf.org/html/rfc6749) server implementation may be very different(optional/recommended response fields, extended grant) it might me useful to describe your unique implementation within your OAS3 file. It's also very handy to see examples of your token and error response, because RFC6749 is a text document without any pictures or graphs. The example file mentioned before contains description of token endpoints for each authorization grant, consider it as starting point.

Example file omits [authorization endpoint](https://tools.ietf.org/html/rfc6749#section-3.1) endpoint on purpose. I don't know how to describe it with OAS3 since endpoint response isn't JSON(html page). If you have any suggestion please submit an issue to this repo.

Since [RFC 6749 - The OAuth2.0 Authorization Framework - 2.3.1. Client Password](https://tools.ietf.org/html/rfc6749#section-2.3.1) doesn't recommend to send client password in request body then our example expects basic authorization in all endpoints.

## Installation

### Copy Paste
Since it's not actually a code, but markup you can just copy anything you want from [dist/oauth2_endpoints.yml](dist/oauth2_endpoints.yml).

### Composer
Install [Composer - Dependency Manager for PHP](https://getcomposer.org/download/)

Then run in terminal:
```console
composer require ybelenko/oauth2_as_oas3_components
```

Use provided components via `$ref` attribute like:

```yaml
paths:
  /token:
    post:
      summary: Obtain access token with "authorization_code" grant.
      requestBody:
        $ref: './vendor/ybelenko/oauth2_as_oas3_components/dist/components/requestBodies/TokenRequestCodeGrant.yml'
      responses:
        '200':
          $ref: './vendor/ybelenko/oauth2_as_oas3_components/dist/components/responses/OAuth2TokenSuccessResponse.yml'
        '4XX':
          $ref: './vendor/ybelenko/oauth2_as_oas3_components/dist/components/responses/OAuth2TokenErrorResponse.yml'
```

Extended example with refs [dist/oauth2_endpoints_with_refs.yml](dist/oauth2_endpoints_with_refs.yml)

### NPM
[Install NPM and Node.js](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm)

Then run in terminal:
```console
npm i --save oauth2_as_oas3_components
```

Use provided components via `$ref` attribute like:

```yaml
paths:
  /token:
    post:
      summary: Obtain access token with "authorization_code" grant.
      requestBody:
        $ref: './node_modules/oauth2_as_oas3_components/dist/components/requestBodies/TokenRequestCodeGrant.yml'
      responses:
        '200':
          $ref: './node_modules/oauth2_as_oas3_components/dist/components/responses/OAuth2TokenSuccessResponse.yml'
        '4XX':
          $ref: './node_modules/oauth2_as_oas3_components/dist/components/responses/OAuth2TokenErrorResponse.yml'
```

Extended example with refs [dist/oauth2_endpoints_with_refs.yml](dist/oauth2_endpoints_with_refs.yml)

## Contributing

If you have any suggestions please submit an issue.

## License
[MIT License](LICENSE)
