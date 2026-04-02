# eslint-plugin-php-markup

A eslint plugin to process PHP markup.

It can make us get rid of "Unexpected token <" errors in .php files.

## Principle

This plugin just replace every php markup `<? ... ?>` to other text.

## Installation

```sh
npm install --save-dev eslint-plugin-php-markup
```

## Usage

ESLint 8 and before:

Add `php-markup` to the `plugins` section of your `.eslintrc` configuration file.

BTW, it works like a charm together with [`eslint-plugin-html`](https://github.com/BenoitZugmeyer/eslint-plugin-html)!

```js
{
  // ...
  "plugins": [
    "html",
    "php-markup"
  ],
  "settings": {
    "php/php-extensions": [".php"],
    "php/markup-replacement": {"php": "", "=": "0"},
    "php/keep-eol": false,
    "php/remove-whitespace": false,
    "php/remove-empty-line": false,
    "php/remove-php-lint": false
  },
  // ...
}
```

ESLint 9 and onward.

Adapt the following to your `eslint.config.*js` file.

Note for some reason, custom settings currently doesn't work, and a default setting is applied.

```js
...
import html from "eslint-plugin-html";
import php from "eslint-plugin-php-markup";
...
... { files: ["**/*.php"],
  plugins: { html, php },
  processor: php.processor,
  settings: {
    "php/php-extensions": [".php"],
    "php/markup-replacement": {"php": "", "=": "0"},
    "php/keep-eol": false,
    "php/remove-whitespace": false,
    "php/remove-empty-line": false,
    "php/remove-php-lint": false
  },
} ...
...
```

# License

MIT
