---
title: no-plusplus - Rules
layout: doc
edit_link: https://github.com/eslint/eslint/edit/master/docs/rules/no-plusplus.md
---
<!-- Note: No pull requests accepted for this file. See README.md in the root directory for details. -->

# disallow the unary operators `++` and `--` (no-plusplus)

Because the unary `++` and `--` operators are subject to automatic semicolon insertion, differences in whitespace can change semantics of source code.

```js
var i = 10;
var j = 20;

i ++
j
// i = 11, j = 20
```

```js
var i = 10;
var j = 20;

i
++
j
// i = 10, j = 21
```

## Rule Details

This rule disallows the unary operators `++` and `--`.

Examples of **incorrect** code for this rule:

```js
/*eslint no-plusplus: "error"*/

var foo = 0;
foo++;

var bar = 42;
bar--;

for (i = 0; i < l; i++) {
    return;
}
```

Examples of **correct** code for this rule:

```js
/*eslint no-plusplus: "error"*/

var foo = 0;
foo += 1;

var bar = 42;
bar -= 1;

for (i = 0; i < l; i += 1) {
    return;
}
```

## Options

This rule has an object option.

* `"allowForLoopAfterthoughts": true` allows unary operators `++` and `--` in the afterthought (final expression) of a `for` loop.

### allowForLoopAfterthoughts

Examples of **correct** code for this rule with the `{ "allowForLoopAfterthoughts": true }` option:

```js
/*eslint no-plusplus: ["error", { "allowForLoopAfterthoughts": true }]*/

for (i = 0; i < l; i++) {
    return;
}

for (i = 0; i < l; i--) {
    return;
}
```

## Version

This rule was introduced in ESLint 0.0.9.

## Resources

* [Rule source](https://github.com/eslint/eslint/tree/master/lib/rules/no-plusplus.js)
* [Documentation source](https://github.com/eslint/eslint/tree/master/docs/rules/no-plusplus.md)
