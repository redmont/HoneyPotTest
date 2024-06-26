Disclaimer: I developed this smart contract in the 2021 crypto bull run. It might not produce expected results as of now. Use it for learning purpose only.

# HoneyPotTest

A simple contract to check if a token contract is a honeypot or not.

# 🩺 HoneyPotTest

Complete Open Source HoneyPot Checker For BSC

Supports WBNB,BUSD,USDT

Contract Address : 0x77Dd873ad58418c40974016EbB792D2c20A1ABCA

It is a smart contract on bsc. You can check if token contract is honeypot or not.

## HOW TO USE

- Always use callStatic or eth_call to perform the operation because if you don't then you might loose some fund because we want to simulate the buy and sell so static call will just simulate the transaction and return the result without changing any state.
- Make sure you have some funds in your wallet to perform the operation.
- Use try & catch to make sure you won't mess your project runtime.

```javascript
ROUTER = DEX ROUTER ADDRESS
BASE = EX. WBNB, USDT, BUSD
TOKEN = TOKEN CONTRACT ADDRESS

 _.callStatic.testHoneyPot(ROUTER,BASE,TOKEN, {
        value: AMOUNT
});

RESPONSE =
[
  false,
  '...',
  '...',
  BigNumber { _hex: '0x07c5afd2', _isBigNumber: true },
  BigNumber { _hex: '0x07129d70', _isBigNumber: true },
  BigNumber { _hex: '0x0c9195e6e59aa589', _isBigNumber: true },
  BigNumber { _hex: '0x0b42767a8d31f2ec', _isBigNumber: true },
  BigNumber { _hex: '0x0234fe', _isBigNumber: true },
  BigNumber { _hex: '0x067d50', _isBigNumber: true },
  isHoneyPot: false,
  base: '...',
  token: '...',
  estimatedBuy: BigNumber { _hex: '0x07c5afd2', _isBigNumber: true },
  buyAmount: BigNumber { _hex: '0x07129d70', _isBigNumber: true },
  estimatedSell: BigNumber { _hex: '0x0c9195e6e59aa589', _isBigNumber: true },
  sellAmount: BigNumber { _hex: '0x0b42767a8d31f2ec', _isBigNumber: true },
  buyGas: BigNumber { _hex: '0x0234fe', _isBigNumber: true },
  sellGas: BigNumber { _hex: '0x067d50', _isBigNumber: true }
]

let buyTax = Math.round(((parseInt(RESPONSE.estimatedBuy) - parseInt(RESPONSE.buyAmount)) / parseInt(RESPONSE.estimatedBuy)) * 100);
let sellTax = Math.round(((parseInt(RESPONSE.estimatedSell) - parseInt(RESPONSE.sellAmount)) / parseInt(RESPONSE.estimatedSell)) * 100);

//RESPONSE BREAKDOWN
estimatedBuy = estimated amount of token bought
buyAmount = actual amount of token bought
estimatedSell = estimated amount of token sold
sellAmount = actual amount of token sold
buyGas = gas required to buy the token
sellGas = gas required to sell the token

```

## Warning

- ALWAYS use callstatic or eth_call to perform the operation.
- Try this at your own risk. I'm not responsible if you lost your funds. This contract checks only the current state.
- Nothing is perfect. This repo is constantly under development.
- Contract does not hold any token or balance.
- I'm not an expert. I'm always learning and improving myself so if you find any bugs, problems or issues then feel free to contact me.

## Authors

- [@redmont](https://www.github.com/redmont)
