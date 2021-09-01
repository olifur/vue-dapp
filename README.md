# (WIP) vue-dapp

Vue3 composable and component library for building Dapps.

👀 [Demo](https://vue-dapp-demo.netlify.app/)

🌏 [Documentation](https://vue-dapp-docs.netlify.app/)

## Features
- TypeScript by default
- Demo ready to be written using [Vite](https://vitejs.dev/)

## Quick Start

Install dependencies:

```bash
npm install --save ethers vue-dapp

yarn add ethers vue-dapp
```

Add dependencies to your main.js:

```javascript
import { createApp } from 'vue'
import VueDapp from 'vue-dapp'

const app = createApp({...})
app.use(VueDapp, {
  infuraAPI: <your-infura-api> // to enable WalletConnect
})
```

Add the global component to your App.vue:

```vue
<board />
```

Use wallet or board from your .vue files:

```javascript
import { defineComponent, watch } from 'vue'
import { useWallet, useBoard } from 'vue-dapp'

export default defineComponent({
  name: 'App',
  setup() {
    const { address, fixedBalance, isConnected, disconnect, error, network } =
      useWallet()

    // open or close the board
    const { open } = useBoard()

    return {
      network,
      error,
      address,
      isConnected,
      fixedBalance,
      disconnect,
      open,
    }
  },
})
```

Add CDN before main.ts for enabling WalletConnect feature:

```html
<body>
  <div id="app"></div>

  <!-- this line -->
  <script src="https://cdn.jsdelivr.net/npm/@walletconnect/web3-provider@1.6.5/dist/umd/index.min.js"></script>
  <script type="module" src="/src/main.ts"></script>
</body>
```
(More about [issue of walletconnect](https://github.com/chnejohnson/vue-dapp/issues/3))

## Contributing

You are more than welcome to improve this project.

Just submit your changes via pull request and I will review them before merging.

If you are making a fix on the project, you can use the `main` branch and send a pull request.

If you are adding a new features, please create a new branch with a name describing your feature (`my-new-feature`), push to your branch and then submit a pull request.


## License

[MIT](https://opensource.org/licenses/MIT)

Copyright (c) 2021-present, Johnson Chen