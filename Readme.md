# @fastify/url-data

![CI](https://github.com/fastify/fastify-url-data/workflows/CI/badge.svg)
[![NPM version](https://img.shields.io/npm/v/@fastify/url-data.svg?style=flat)](https://www.npmjs.com/package/@fastify/url-data)
[![js-standard-style](https://img.shields.io/badge/code%20style-standard-brightgreen.svg?style=flat)](https://standardjs.com/)

A plugin for [Fastify](https://fastify.dev/) that adds support for getting raw
URL information from the request.

## Example

```js
const fastify = require('fastify')()

fastify.register(require('@fastify/url-data'))

fastify.get('/foo', (req, reply) => {
  const urlData = req.urlData()
  req.log.info(urlData.pathname) // '/foo'
  req.log.info(urlData.search) // '?a=b&c=d'
  req.log.info(urlData.hostname) // '127.0.0.1'
  req.log.info(urlData.port) // 8080

  // if you just need single data:
  req.log.info(req.urlData('pathname')) // '/foo'

  reply.send({hello: 'world'})
})

// GET: 'http://127.0.0.1:8080/foo?a=b&c=d
```

## License

Licensed under [MIT](./LICENSE)
