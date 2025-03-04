# decamelize-keys

> Convert object keys from camel case using [`decamelize`](https://github.com/sindresorhus/decamelize)

## Install

```sh
npm install decamelize-keys
```

## Usage

```js
import decamelizeKeys from 'decamelize-keys';

// Convert an object
decamelizeKeys({fooBar: true});
//=> {foo_bar: true}

// Convert an array of objects
decamelizeKeys([{fooBar: true}, {barFoo: false}]);
//=> [{foo_bar: true}, {bar_foo: false}]
```

## API

### decamelizeKeys(input, options?)

#### input

Type: `object | object[]`

An object or array of objects to decamelize.

#### options

Type: `object`

##### separator

Type: `string`\
Default: `'_'`

The character or string used to separate words.

```js
import decamelizeKeys from 'decamelize-keys';

decamelizeKeys({fooBar: true});
//=> {foo_bar: true}

decamelizeKeys({fooBar: true}, {separator: '-'});
//=> {'foo-bar': true}
```

##### exclude

Type: `Array<string | RegExp>`\
Default: `[]`

Exclude keys from being decamelized.

#### stopPaths
Type: `string`\
Default: `[]`

Exclude children at the given object paths in dot-notation from being decamel-cased. For example, with an object like {a: {b: '🦄'}}, the object path to reach the unicorn is 'a.b'.

```
decamelizeKeys({
	aB: 1,
	aC: {
		cD: 1,
		cE: {
			eF: 1
		}
	}
}, {
	deep: true,
	stopPaths: [
		'aC.cE'
	]
}),
/*
{
	a_b: 1,
	a_c: {
		c_d: 1,
		c_e: {
			eF: 1
		}
	}
}
*/
```

##### deep

Type: `boolean`\
Default: `false`

Recurse nested objects and objects in arrays.

```js
import decamelizeKeys from 'decamelize-keys';

decamelizeKeys({fooBar: true, nested: {unicornRainbow: true}}, {deep: true});
//=> {foo_bar: true, nested: {unicorn_rainbow: true}}
```

## Related

- [camelcase-keys](https://github.com/sindresorhus/camelcase-keys) - The inverse of this package.
