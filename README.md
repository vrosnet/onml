# ONML
[![NPM version](https://img.shields.io/npm/v/onml.svg)](https://www.npmjs.org/package/onml) [![Build Status](https://travis-ci.org/drom/onml.svg?branch=master)](https://travis-ci.org/drom/onml) [![Build status](https://ci.appveyor.com/api/projects/status/pcxe8l0w97jwfmil?svg=true)](https://ci.appveyor.com/project/drom/onml)

[jsonml.org](http://www.jsonml.org/) compatible tool set.

## Use
### Node.js

```
npm i onml --save
```

```js
var onml = require('onml');
```

## API
### onml.parse() --- onml.p()
The `onml.parse()` method parses a XML/HTML/SVG string and returns a JavaScript value.

```js
var obj = onml.parse('<text a="5">so me<text>');
console.log(obj);
-->
["text", {a: "5"}, "so me"]
```

### onml.stringify() --- onml.s()
The `onml.stringify()` method converts a JavaScript value to a XML/HTML/SVG string.

```js
var str = onml.stringify(['text', {a: '55'}, 'so me']);
console.log(str);
-->
<text a="55">
  so me
</text>
```

### onml.traverse() --- onml.t()
JSONML object traversal tool. See [test/traverse.js](test/traverse.js) for more details.

```js
// count divs on enter
var count = 0;
onml.traverse(
    ['b',
        ['div', {a: true},
            ['span',
                'div',
                ['div',
                    ['div', {},
                        ['div', {a: true}]
                    ]
                ],
                ['div', {},
                    ['div']
                ]
            ]
        ]
    ],
    {
        enter: function (node) {
            if (node.name === 'div') {
                count++;
            }
        }
    }
);
console.log(count);
-->
6
```

## Testing
`npm test`

## License
MIT [LICENSE](https://github.com/drom/onml/blob/master/LICENSE).