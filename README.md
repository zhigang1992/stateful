# @zhigang1992/stateful

> Stateful Wrapper for not having to write react classes

[![NPM](https://img.shields.io/npm/v/@zhigang1992/stateful.svg)](https://www.npmjs.com/package/@zhigang1992/stateful) [![JavaScript Style Guide](https://img.shields.io/badge/code_style-standard-brightgreen.svg)](https://standardjs.com)

## Install

```bash
npm install --save @zhigang1992/stateful
```

## Usage

```jsx
import React, { Component, Fragment } from 'react'

import Stateful, {Onmount} from '@zhigang1992/stateful'

export default class App extends Component {
  render() {
    return (
      <Stateful state={{count: 0, seconds: 0}}>
        {({ state, setState, getState }) => (
          <Fragment>
            <p>Clicked {state.count} times</p>
            <button onClick={() => setState({ count: state.count + 1 })}>
              Click me
            </button>
            <p>{state.seconds} seconds passed</p>
            <Onmount>{() => {
              // You can do stuff like firing a network request in here
              window.setInterval(() => {
                setState({seconds: getState().seconds + 1})
              }, 1000)
            }}</Onmount>
          </Fragment>
        )}
      </Stateful>
    )
  }
}
```

## License

MIT © [zhigang1992](https://github.com/zhigang1992)
