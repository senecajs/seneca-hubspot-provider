![Seneca](http://senecajs.org/files/assets/seneca-logo.png)
> A [Seneca.js](http://senecajs.org) plugin

# @seneca/hubspot-provider

[![build](https://github.com/senecajs/seneca-hubspot-provider/actions/workflows/build.yml/badge.svg)](https://github.com/senecajs/seneca-hubspot-provider/actions/workflows/build.yml)
[![Known Vulnerabilities](https://snyk.io/test/github/senecajs/seneca-hubspot-provider/badge.svg)](https://snyk.io/test/github/senecajs/seneca-hubspot-provider)

| ![Voxgig](https://www.voxgig.com/res/img/vgt01r.png) | This open source module is sponsored and supported by [Voxgig](https://www.voxgig.com). |
|---|---|

## Install

```sh
$ npm install @seneca/hubspot-provider
```



<!--START:options-->

## Quick Example

```js

// Setup - get the key value (<SECRET>) separately from a vault or
// environment variable.
Seneca()
  .use('env', { // the 'env' plugin enables you to use environment variables in your Seneca instance.
    // debug: true,
    file: [__dirname + '/local-env.js;?'], // you can specify the file with your company's data such as id, etc.
    var: {
      $HUBSPOT_ACCESS_TOKEN: '<SECRET>',
    }
  })
  .use('provider', {
    provider: {
      hubspot: {
        keys: {
          accessToken: {
            value: '$HUBSPOT_ACCESS_TOKEN'
          },
        }
      }
    }
  })
  .use('hubspot-provider')

let companyId = await seneca.entity('provider/hubspot/company')
  .load$('id')
  // .load({id: 'id', fields$: ['state', 'city', 'description']}); // you can use fields$_directive to specify the properties you want to get from a company

Console.log('COMPANY DATA', companyId)

companyId.properties.description = 'New description'
companyId = await companyId.save$()

Console.log('UPDATED DATA', companyId)

```

## More Examples

See [test/](test/) for more usage examples.

## Motivation

A [Seneca.js](http://senecajs.org) plugin.

## Support

If you're using this module and need help, you can:

- Post a [github issue](https://github.com/senecajs/seneca-hubspot-provider/issues)
- Tweet to [@senecajs](http://twitter.com/senecajs)
- Ask on the [Gitter](https://gitter.im/senecajs/seneca)

## API

### Options

*None.*


<!--END:options-->

<!--START:action-list-->

### Action Patterns

* ["role":"entity","base":"hubspot","cmd":"list","name":"company","zone":"provider"](#-roleentitybasehubspotcmdlistnamecompanyzoneprovider-)
* ["role":"entity","base":"hubspot","cmd":"load","name":"company","zone":"provider"](#-roleentitybasehubspotcmdloadnamecompanyzoneprovider-)
* ["role":"entity","base":"hubspot","cmd":"save","name":"company","zone":"provider"](#-roleentitybasehubspotcmdsavenamecompanyzoneprovider-)
* ["sys":"provider","get":"info","provider":"hubspot"](#-sysprovidergetinfoproviderhubspot-)


<!--END:action-list-->

<!--START:action-desc-->

### Action Descriptions

### &laquo; `"role":"entity","base":"hubspot","cmd":"list","name":"company","zone":"provider"` &raquo;

List Hubspot data into an entity.



----------
### &laquo; `"role":"entity","base":"hubspot","cmd":"load","name":"company","zone":"provider"` &raquo;

Load Hubspot data into an entity.



----------
### &laquo; `"role":"entity","base":"hubspot","cmd":"save","name":"company","zone":"provider"` &raquo;

Update/Save Hubspot data into an entity



----------
### &laquo; `"sys":"provider","get":"info","provider":"hubspot"` &raquo;

Get information about the provider.



----------


<!--END:action-desc-->

## Contributing

The [Senecajs org](https://github.com/senecajs/) encourages open participation. If you feel you can help in any way, be it with documentation, examples, extra testing, or new features please get in touch.

### Running tests

```sh
npm run test
```

## Background

Part of the [Senecajs org](https://github.com/senecajs/).
