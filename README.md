# api documentation for  [twemoji (v2.2.5)](https://github.com/twitter/twemoji)  [![npm package](https://img.shields.io/npm/v/npmdoc-twemoji.svg?style=flat-square)](https://www.npmjs.org/package/npmdoc-twemoji) [![travis-ci.org build-status](https://api.travis-ci.org/npmdoc/node-npmdoc-twemoji.svg)](https://travis-ci.org/npmdoc/node-npmdoc-twemoji)
#### A Unicode 9 standard based way to implement emoji across all platforms.

[![NPM](https://nodei.co/npm/twemoji.png?downloads=true)](https://www.npmjs.com/package/twemoji)

[![apidoc](https://npmdoc.github.io/node-npmdoc-twemoji/build/screenCapture.buildNpmdoc.browser._2Fhome_2Ftravis_2Fbuild_2Fnpmdoc_2Fnode-npmdoc-twemoji_2Ftmp_2Fbuild_2Fapidoc.html.png)](https://npmdoc.github.io/node-npmdoc-twemoji/build/apidoc.html)

![npmPackageListing](https://npmdoc.github.io/node-npmdoc-twemoji/build/screenCapture.npmPackageListing.svg)

![npmPackageDependencyTree](https://npmdoc.github.io/node-npmdoc-twemoji/build/screenCapture.npmPackageDependencyTree.svg)



# package.json

```json

{
    "author": {
        "name": "Twitter, Inc.",
        "url": "https://github.com/twitter/"
    },
    "bugs": {
        "url": "https://github.com/twitter/twemoji/issues"
    },
    "dependencies": {},
    "description": "A Unicode 9 standard based way to implement emoji across all platforms.",
    "devDependencies": {
        "phantomjs-prebuilt": "2.1.4",
        "uglify-js": "2.6.2"
    },
    "directories": {},
    "dist": {
        "shasum": "116907bff0c95b56b6414857c5d8588972a52956",
        "tarball": "https://registry.npmjs.org/twemoji/-/twemoji-2.2.5.tgz"
    },
    "gitHead": "a142e43842f1cb619493b4ee6c17631320289ea1",
    "homepage": "https://github.com/twitter/twemoji",
    "keywords": [
        "emoji",
        "DOM",
        "parser",
        "images",
        "retina",
        "Twitter",
        "unicode"
    ],
    "license": [
        "MIT",
        "CC-BY-4.0"
    ],
    "main": "./2/twemoji.npm.js",
    "maintainers": [
        {
            "name": "bhaggs",
            "email": "bryan@bryanhaggerty.com"
        },
        {
            "name": "webreflection",
            "email": "andrea.giammarchi@gmail.com"
        }
    ],
    "name": "twemoji",
    "optionalDependencies": {},
    "readme": "ERROR: No README data found!",
    "repository": {
        "type": "git",
        "url": "git://github.com/twitter/twemoji.git"
    },
    "scripts": {
        "test": "phantomjs testrunner.js"
    },
    "version": "2.2.5"
}
```



# <a name="apidoc.tableOfContents"></a>[table of contents](#apidoc.tableOfContents)

#### [module twemoji](#apidoc.module.twemoji)
1.  [function <span class="apidocSignatureSpan">twemoji.</span>onerror ()](#apidoc.element.twemoji.onerror)
1.  [function <span class="apidocSignatureSpan">twemoji.</span>parse (what, how)](#apidoc.element.twemoji.parse)
1.  [function <span class="apidocSignatureSpan">twemoji.</span>replace (text, callback)](#apidoc.element.twemoji.replace)
1.  [function <span class="apidocSignatureSpan">twemoji.</span>test (text)](#apidoc.element.twemoji.test)
1.  object <span class="apidocSignatureSpan">twemoji.</span>convert
1.  string <span class="apidocSignatureSpan">twemoji.</span>base
1.  string <span class="apidocSignatureSpan">twemoji.</span>className
1.  string <span class="apidocSignatureSpan">twemoji.</span>ext
1.  string <span class="apidocSignatureSpan">twemoji.</span>size

#### [module twemoji.convert](#apidoc.module.twemoji.convert)
1.  [function <span class="apidocSignatureSpan">twemoji.convert.</span>fromCodePoint (codepoint)](#apidoc.element.twemoji.convert.fromCodePoint)
1.  [function <span class="apidocSignatureSpan">twemoji.convert.</span>toCodePoint (unicodeSurrogates, sep)](#apidoc.element.twemoji.convert.toCodePoint)



# <a name="apidoc.module.twemoji"></a>[module twemoji](#apidoc.module.twemoji)

#### <a name="apidoc.element.twemoji.onerror"></a>[function <span class="apidocSignatureSpan">twemoji.</span>onerror ()](#apidoc.element.twemoji.onerror)
- description and source-code
```javascript
function onerror() {
  if (this.parentNode) {
    this.parentNode.replaceChild(createText(this.alt), this);
  }
}
```
- example usage
```shell
n/a
```

#### <a name="apidoc.element.twemoji.parse"></a>[function <span class="apidocSignatureSpan">twemoji.</span>parse (what, how)](#apidoc.element.twemoji.parse)
- description and source-code
```javascript
function parse(what, how) {
  if (!how || typeof how === 'function') {
    how = {callback: how};
  }
  // if first argument is string, inject html <img> tags
  // otherwise use the DOM tree and parse text nodes only
  return (typeof what === 'string' ? parseString : parseNode)(what, {
    callback:   how.callback || defaultImageSrcGenerator,
    attributes: typeof how.attributes === 'function' ? how.attributes : returnNull,
    base:       typeof how.base === 'string' ? how.base : twemoji.base,
    ext:        how.ext || twemoji.ext,
    size:       how.folder || toSizeSquaredAsset(how.size || twemoji.size),
    className:  how.className || twemoji.className,
    onerror:    how.onerror || twemoji.onerror
  });
}
```
- example usage
```shell
...
Everything else is pretty much the same, so if you were using the defaults, all you need to do is to add the version '2/' before
 the 'twemoji.js' file you were using.


## API

Following are all the methods exposed in the 'twemoji' namespace.

### twemoji.parse( ... ) V1

This is the main parsing utility and has 3 overloads per parsing type.

There are mainly two kinds of parsing: [string parsing](https://github.com/twitter/twemoji#string-parsing) and [DOM parsing](https
://github.com/twitter/twemoji#dom-parsing).

Each of them accepts a callback to generate an image source or an options object with parsing info.
...
```

#### <a name="apidoc.element.twemoji.replace"></a>[function <span class="apidocSignatureSpan">twemoji.</span>replace (text, callback)](#apidoc.element.twemoji.replace)
- description and source-code
```javascript
function replace(text, callback) {
  return String(text).replace(re, callback);
}
```
- example usage
```shell
...
* This is the most raw version used by
*  the .parse(string) method itself.
*
* @param   string    generic string to parse
* @param   Function  a generic callback that will be
*                    invoked to replace the content.
*                    This calback wil receive standard
*                    String.prototype.replace(str, callback)
*                    arguments such:
*  callback(
*    rawText,  // the emoji match
*  );
*
*                    and others commonly received via replace.
*/
...
```

#### <a name="apidoc.element.twemoji.test"></a>[function <span class="apidocSignatureSpan">twemoji.</span>test (text)](#apidoc.element.twemoji.test)
- description and source-code
```javascript
function test(text) {
  // IE6 needs a reset before too
  re.lastIndex = 0;
  var result = re.test(text);
  re.lastIndex = 0;
  return result;
}
```
- example usage
```shell
...
   * Simplify string tests against emoji.
   *
   * @param   string  some text that might contain emoji
   * @return  boolean true if any emoji was found, false otherwise.
   *
   * @example
   *
   *  if (twemoji.test(someContent)) {
   *    console.log("emoji All The Things!");
   *  }
   */
  test: test
},

// used to escape HTML special chars in attributes
...
```



# <a name="apidoc.module.twemoji.convert"></a>[module twemoji.convert](#apidoc.module.twemoji.convert)

#### <a name="apidoc.element.twemoji.convert.fromCodePoint"></a>[function <span class="apidocSignatureSpan">twemoji.convert.</span>fromCodePoint (codepoint)](#apidoc.element.twemoji.convert.fromCodePoint)
- description and source-code
```javascript
function fromCodePoint(codepoint) {
  var code = typeof codepoint === 'string' ?
        parseInt(codepoint, 16) : codepoint;
  if (code < 0x10000) {
    return fromCharCode(code);
  }
  code -= 0x10000;
  return fromCharCode(
    0xD800 + (code >> 10),
    0xDC00 + (code & 0x3FF)
  );
}
```
- example usage
```shell
...
'''
This will generate urls such 'https://twemoji.maxcdn.com/svg/2764.svg' instead of using a specific size based image.

## Utilities

Basic utilities / helpers to convert code points to JavaScript surrogates and vice versa.

#### twemoji.convert.fromCodePoint()
For a given HEX codepoint, returns UTF-16 surrogate pairs.
'''js
twemoji.convert.fromCodePoint('1f1e8');
 // "\ud83c\udde8"
'''
#### twemoji.convert.toCodePoint()
For given UTF-16 surrogate pairs, returns the equivalent HEX codepoint.
...
```

#### <a name="apidoc.element.twemoji.convert.toCodePoint"></a>[function <span class="apidocSignatureSpan">twemoji.convert.</span>toCodePoint (unicodeSurrogates, sep)](#apidoc.element.twemoji.convert.toCodePoint)
- description and source-code
```javascript
function toCodePoint(unicodeSurrogates, sep) {
  var
    r = [],
    c = 0,
    p = 0,
    i = 0;
  while (i < unicodeSurrogates.length) {
    c = unicodeSurrogates.charCodeAt(i++);
    if (p) {
      r.push((0x10000 + ((p - 0xD800) << 10) + (c - 0xDC00)).toString(16));
      p = 0;
    } else if (0xD800 <= c && c <= 0xDBFF) {
      p = c;
    } else {
      r.push(c.toString(16));
    }
  }
  return r.join(sep || '-');
}
```
- example usage
```shell
...

#### twemoji.convert.fromCodePoint()
For a given HEX codepoint, returns UTF-16 surrogate pairs.
'''js
twemoji.convert.fromCodePoint('1f1e8');
// "\ud83c\udde8"
'''
#### twemoji.convert.toCodePoint()
For given UTF-16 surrogate pairs, returns the equivalent HEX codepoint.
'''js
twemoji.convert.toCodePoint('\ud83c\udde8\ud83c\uddf3');
// "1f1e8-1f1f3"

twemoji.convert.toCodePoint('\ud83c\udde8\ud83c\uddf3', '~');
// "1f1e8~1f1f3"
...
```



# misc
- this document was created with [utility2](https://github.com/kaizhu256/node-utility2)
