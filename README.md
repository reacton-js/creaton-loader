## creaton-loader

![creaton](https://raw.githubusercontent.com/reacton-js/creaton/main/logo.png)

Loader for single-file [Creaton](https://www.npmjs.com/package/creaton-js) components in [Webpack](https://webpack.js.org/)

### Install

```
npm i creaton-loader -D
```

**webpack.config.js**

```js
module: {
  rules: [
    {
      test: /\.html?$/,
      loader: 'creaton-loader'
    }
    ... // other rules
  ]
},
```

**example Component.htm**

```html
<h2>${ this.title }</h2>
<p>${ this.message }</p>

<script>
  import { httpRequest } from '../helpers'

  exports = class WHome {
    static mode = 'open'

    static async startConnect() {
      const home = await httpRequest('/db?page=home')
      this.title = home.title
      this.message = home.message
    }

    static template() {
      return `
        <h2>${ this.title }</h2>
        <p>${ this.message }</p>
      `
    }
  }
</script>
```