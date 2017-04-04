# api documentation for  [good (v7.1.0)](https://github.com/hapijs/good#readme)  [![npm package](https://img.shields.io/npm/v/npmdoc-good.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-good) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-good.svg)](https://travis-ci.org/npmdoc/node-npmdoc-good)
#### Server and process monitoring plugin

[![NPM](https://nodei.co/npm/good.png?downloads=true)](https://www.npmjs.com/package/good)

[![apidoc](https://npmdoc.github.io/node-npmdoc-good/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-good_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-good/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-good/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-good/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "bugs": {
        "url": "https://github.com/hapijs/good/issues"
    },
    "dependencies": {
        "hoek": "4.x.x",
        "joi": "10.x.x",
        "oppsy": "1.x.x",
        "pumpify": "1.3.x"
    },
    "description": "Server and process monitoring plugin",
    "devDependencies": {
        "async": "2.1.x",
        "code": "4.x.x",
        "hapi": "16.x.x",
        "lab": "11.x.x",
        "wreck": "10.x.x"
    },
    "directories": {},
    "dist": {
        "shasum": "9e05ad24c58a11b71cf5081700f3778db0b22c1c",
        "tarball": "https://registry.npmjs.org/good/-/good-7.1.0.tgz"
    },
    "engines": {
        "node": ">=4.0.0"
    },
    "gitHead": "f0b562e09f3b82f0680a6018eaaae286cf4cece8",
    "homepage": "https://github.com/hapijs/good#readme",
    "keywords": [
        "process",
        "monitor",
        "log",
        "report",
        "hapi",
        "plugin"
    ],
    "license": "BSD-3-Clause",
    "main": "lib/index.js",
    "maintainers": [
        {
            "name": "hueniverse",
            "email": "eran@hammer.io"
        },
        {
            "name": "wyatt",
            "email": "wpreul@gmail.com"
        },
        {
            "name": "arb",
            "email": "arbretz@gmail.com"
        },
        {
            "name": "lloydbenson",
            "email": "lloyd.benson@gmail.com"
        }
    ],
    "name": "good",
    "optionalDependencies": {},
    "peerDependencies": {
        "hapi": ">=10.x.x"
    },
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/hapijs/good.git"
    },
    "scripts": {
        "test": "lab -m 5000 -t 100 -v -La code"
    },
    "version": "7.1.0"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module good](#apidoc.module.good)
1.  [function <span class="apidocSignatureSpan">good.</span>register (server, options, next)](#apidoc.element.good.register)
1.  object <span class="apidocSignatureSpan">good.</span>utils

#### [module good.utils](#apidoc.module.good.utils)
1.  [function <span class="apidocSignatureSpan">good.utils.</span>NoOp ()](#apidoc.element.good.utils.NoOp)
1.  [function <span class="apidocSignatureSpan">good.utils.</span>Ops (ops)](#apidoc.element.good.utils.Ops)
1.  [function <span class="apidocSignatureSpan">good.utils.</span>RequestError (request, error)](#apidoc.element.good.utils.RequestError)
1.  [function <span class="apidocSignatureSpan">good.utils.</span>RequestLog (request, event)](#apidoc.element.good.utils.RequestLog)
1.  [function <span class="apidocSignatureSpan">good.utils.</span>RequestSent (reqOptions, resOptions, request)](#apidoc.element.good.utils.RequestSent)
1.  [function <span class="apidocSignatureSpan">good.utils.</span>ServerLog (event)](#apidoc.element.good.utils.ServerLog)
1.  [function <span class="apidocSignatureSpan">good.utils.</span>WreckResponse (error, request, response, start, uri)](#apidoc.element.good.utils.WreckResponse)



# <a name="apidoc.module.good"></a>[module good](#apidoc.module.good)

#### <a name="apidoc.element.good.register"></a>[function <span class="apidocSignatureSpan">good.</span>register (server, options, next)](#apidoc.element.good.register)
- description and source-code
```javascript
(server, options, next) => {

    const result = Joi.validate(options, Schema.monitor);
    Hoek.assert(!result.error, 'Invalid', 'monitorOptions', 'options', result.error);

    const monitor = new Monitor(server, result.value);
    server.ext([{
        type: 'onPostStop',
        method: internals.onPostStop(monitor)
    }, {
        type: 'onPreStart',
        method: internals.onPreStart(monitor, result.value)
    }]);

    return monitor.start(next);
}
```
- example usage
```shell
...
                headers: { 'x-api-key': 12345 }
            }
        }]
    }]
}
};

server.register({
register: require('good'),
options,
}, (err) => {

if (err) {
    return console.error(err);
}
...
```



# <a name="apidoc.module.good.utils"></a>[module good.utils](#apidoc.module.good.utils)

#### <a name="apidoc.element.good.utils.NoOp"></a>[function <span class="apidocSignatureSpan">good.utils.</span>NoOp ()](#apidoc.element.good.utils.NoOp)
- description and source-code
```javascript
class NoOp extends Stream.Transform {
    constructor() {

        super({ objectMode: true });
    }
    _transform(value, encoding, callback) {

        callback(null, value);
    }
}
```
- example usage
```shell
...
    const stream = new Ctor();
    Hoek.assert(typeof stream.pipe === 'function', 'Error in ${reporterName}. ${moduleName} must create a stream that has a pipe
 function.');

    streamObjs.push(stream);
}

if (streamObjs.length === 1) {
    streamObjs.unshift(new Utils.NoOp());
}

this._reporters[reporterName] = Pumpify.obj(streamObjs);
this._reporters[reporterName].on('error', (err) => {

    console.error('There was a problem (${err}) in ${reporterName} and it has been destroyed.');
});
...
```

#### <a name="apidoc.element.good.utils.Ops"></a>[function <span class="apidocSignatureSpan">good.utils.</span>Ops (ops)](#apidoc.element.good.utils.Ops)
- description and source-code
```javascript
class Ops {
    constructor(ops) {

        this.event = 'ops';
        this.timestamp = Date.now();
        this.host = ops.host;
        this.pid = process.pid;
        this.os = {
            load: ops.osload,
            mem: ops.osmem,
            uptime: ops.osup
        };
        this.proc = {
            uptime: ops.psup,
            mem: ops.psmem,
            delay: ops.psdelay
        };
        this.load = {
            requests: ops.requests,
            concurrents: ops.concurrents,
            responseTimes: ops.responseTimes,
            sockets: ops.sockets
        };
    }
}
```
- example usage
```shell
...
        this._responseHandler = (request) => {

this.push(() => new Utils.RequestSent(reqOptions, resOptions, request));
        };

        this._opsHandler = (results) => {

this.push(() => new Utils.Ops(results));
        };

        if (this.settings.wreck) {
this._wreckHandler = (error, request, response, start, uri) => {

    this.push(() => new Utils.WreckResponse(error, request, response, start, uri));
};
...
```

#### <a name="apidoc.element.good.utils.RequestError"></a>[function <span class="apidocSignatureSpan">good.utils.</span>RequestError (request, error)](#apidoc.element.good.utils.RequestError)
- description and source-code
```javascript
class RequestError {
    constructor(request, error) {

        this.event = 'error';
        this.timestamp = request.info.received;
        this.id = request.id;
        this.url = request.url;
        this.method = request.method;
        this.pid = process.pid;
        this.error = error;
        this.config = internals.extractConfig(request);
    }
    toJSON() {

        const result = Object.assign({}, this, {
            error: {
                error: this.error.message,
                stack: this.error.stack
            }
        });
        return result;
    }
}
```
- example usage
```shell
...
this._logHandler = (event) => {

    this.push(() => new Utils.ServerLog(event));
};

this._errorHandler = (request, error) => {

    this.push(() => new Utils.RequestError(request, error));
};

this._responseHandler = (request) => {

    this.push(() => new Utils.RequestSent(reqOptions, resOptions, request));
};
...
```

#### <a name="apidoc.element.good.utils.RequestLog"></a>[function <span class="apidocSignatureSpan">good.utils.</span>RequestLog (request, event)](#apidoc.element.good.utils.RequestLog)
- description and source-code
```javascript
class RequestLog {
    constructor(request, event) {

        this.event = 'request';
        this.timestamp = event.timestamp;
        this.tags = event.tags;
        this.data = event.data;
        this.pid = process.pid;
        this.id = request.id;
        this.method = request.method;
        this.path = request.path;
        this.config = internals.extractConfig(request);
    }
}
```
- example usage
```shell
...

this._ops = this.settings.ops && new Oppsy(server, this.settings.ops.config);

// Event handlers

this._requestLogHandler = (request, event) => {

    this.push(() => new Utils.RequestLog(request, event));
};

this._logHandler = (event) => {

    this.push(() => new Utils.ServerLog(event));
};
...
```

#### <a name="apidoc.element.good.utils.RequestSent"></a>[function <span class="apidocSignatureSpan">good.utils.</span>RequestSent (reqOptions, resOptions, request)](#apidoc.element.good.utils.RequestSent)
- description and source-code
```javascript
class RequestSent {
    constructor(reqOptions, resOptions, request) {

        const req = request.raw.req;
        const res = request.raw.res;

        this.event = 'response';
        this.timestamp = request.info.received;
        this.id = request.id;
        this.instance = request.connection.info.uri;
        this.labels = request.connection.settings.labels;
        this.method = request.method;
        this.path = request.path;
        this.query = request.query;
        this.responseTime = Date.now() - request.info.received;
        this.responseSentTime = request.info.responded - request.info.received;
        this.statusCode = res.statusCode;
        this.pid = process.pid;
        this.httpVersion = request.raw.req.httpVersion;
        this.source = {
            remoteAddress: request.info.remoteAddress,
            userAgent: req.headers['user-agent'],
            referer: req.headers.referer
        };
        this.route = request.route.path;

<span class="apidocCodeCommentSpan">        /* $lab:coverage:off$ */
</span>        this.log = (request.route.settings.log === false ? [] : request.getLog());          // Explicitly compare to false for hapi
 < v15
        /* $lab:coverage:on$ */

        this.tags = request.route.settings.tags;

        if (reqOptions.headers) {
            this.headers = req.headers;
        }

        if (reqOptions.payload) {
            this.requestPayload = request.payload;
        }

        if (resOptions.payload && request.response) {
            this.responsePayload = request.response.source;
        }
        this.config = internals.extractConfig(request);
    }
}
```
- example usage
```shell
...
this._errorHandler = (request, error) => {

    this.push(() => new Utils.RequestError(request, error));
};

this._responseHandler = (request) => {

    this.push(() => new Utils.RequestSent(reqOptions, resOptions, request));
};

this._opsHandler = (results) => {

    this.push(() => new Utils.Ops(results));
};
...
```

#### <a name="apidoc.element.good.utils.ServerLog"></a>[function <span class="apidocSignatureSpan">good.utils.</span>ServerLog (event)](#apidoc.element.good.utils.ServerLog)
- description and source-code
```javascript
class ServerLog {
    constructor(event) {

        this.event = 'log';
        this.timestamp = event.timestamp;
        this.tags = event.tags;
        this.data = event.data;
        this.pid = process.pid;
    }
}
```
- example usage
```shell
...
this._requestLogHandler = (request, event) => {

    this.push(() => new Utils.RequestLog(request, event));
};

this._logHandler = (event) => {

    this.push(() => new Utils.ServerLog(event));
};

this._errorHandler = (request, error) => {

    this.push(() => new Utils.RequestError(request, error));
};
...
```

#### <a name="apidoc.element.good.utils.WreckResponse"></a>[function <span class="apidocSignatureSpan">good.utils.</span>WreckResponse (error, request, response, start, uri)](#apidoc.element.good.utils.WreckResponse)
- description and source-code
```javascript
class WreckResponse {
    constructor(error, request, response, start, uri) {

        response = response || {};
        uri = uri || {};
        this.event = 'wreck';
        this.timestamp = Date.now();
        this.timeSpent = this.timestamp - start;
        this.pid = process.pid;

        if (error) {
            this.error = {
                message: error.message,
                stack: error.stack
            };
        }

        this.request = {
            method: uri.method,
            path: uri.path,
            url: uri.href,
            protocol: uri.protocol,
            host: uri.host,
            headers: request._headers
        };

        this.response = {
            statusCode: response.statusCode,
            statusMessage: response.statusMessage,
            headers: response.headers
        };
    }
}
```
- example usage
```shell
...

        this.push(() => new Utils.Ops(results));
    };

    if (this.settings.wreck) {
        this._wreckHandler = (error, request, response, start, uri) => {

            this.push(() => new Utils.WreckResponse(error, request, response, start, uri));
        };
    }

}

startOps(interval) {
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
