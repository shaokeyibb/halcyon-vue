# halcyon 🌅

[![npm](https://img.shields.io/npm/v/halcyon-vue?style=flat-square)](https://www.npmjs.com/package/halcyon-vue)
[![docs](https://img.shields.io/badge/docs-green?style=flat-square)][halcyon-docs]

A [Material You][m3] plugin and component library for [Vite] / [Vue 3][v3].

> **Warning**
> This is extremely early in development.

## Installation and usage

Add the package to your project:

```sh
pnpm add halcyon-vue
```

Load the plugin in your Vite setup:

```ts
import { defineConfig } from 'vite'
import { Halcyon } from 'halcyon-vue/plugin'
import theme from './theme.json'
// ...
export default defineConfig({
    plugins: [
        // ...
        Halcyon({ theme })
    ]
})
```

Import the stylesheets:

```ts
// main.ts
import 'halcyon:reset.css' // optional if you're already using a css reset
import 'halcyon:theme.css' // sets up the theme variables
import 'halcyon:base.css'  // includes global styles (e.g. body)
import 'halcyon-vue/style' // includes component styles
```

Now you can use the components however you should wish:

```html
<script setup>
import { HButton } from 'halcyon-vue'

const alert = (msg) => window.alert(msg) // vue why
</script>
<template>
    <div>
        <HButton
            kind="filled"
            content="Press me!"
            @click="alert('yippee')"
        />
    </div>
</template>
```

[You can browse our documentation online!][halcyon-docs]

### Generating a Theme

You should use the [Material Theme Builder][theme-builder] to generate a theme.
From there, download the JSON - you can then use the theme in Halcyon by passing it
into the plugin.

### Overriding the theme

The theme variables are just CSS variables, so you can replace them in your
own CSS:

```css
.this-part-is-very-red {
    --halcyon-primary: #ff0000;
}
```

### Fonts

It's not required, but you should import a couple fonts for the most accurate
experience. In particular, [Roboto Flex][roboto-flex] (or [Roboto] if your target
doesn't support variable fonts) and [Noto Sans][noto-sans] (as a fallback font)
are used. Here's a snippet you can put into your `index.html` to import Roboto Flex
and Noto Sans:

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Noto+Sans:ital,wght@0,400;0,500;0,700;1,400;1,500;1,700&family=Roboto+Flex:wght@400;500;700&display=swap" rel="stylesheet">
```

(This snippet probably imports more than you'll need, so consider selecting the
fonts on Google Fonts yourself.)

### Icons

You should use [unplugin-icons] for Material Design icons. It's what the docs
use, and it's the only thing tested with.

## License

[MIT][license]

[vite]: https://vitejs.dev
[m3]: https://m3.material.io
[v3]: https://vuejs.org
[theme-builder]: https://www.figma.com/community/plugin/1034969338659738588/Material-Theme-Builder
[roboto-flex]: https://fonts.google.com/specimen/Roboto+Flex
[roboto]: https://fonts.google.com/specimen/Roboto
[noto-sans]: https://fonts.google.com/noto/specimen/Noto+Sans?query=noto
[license]: https://github.com/halcyon-vue/halcyon-vue/blob/main/LICENSE
[halcyon-docs]: https://halcyon-vue.github.io/halcyon-vue
[unplugin-icons]: https://github.com/antfu/unplugin-icons
