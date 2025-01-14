# bot-o-tron
[![Build Status](https://travis-ci.org/tailuge/bot-o-tron.svg?branch=master)](https://travis-ci.org/tailuge/bot-o-tron/) [![Coverage Status](https://coveralls.io/repos/github/tailuge/bot-o-tron/badge.svg?branch=master)](https://coveralls.io/github/tailuge/bot-o-tron?branch=master) [![CodeFactor](https://www.codefactor.io/repository/github/tailuge/bot-o-tron/badge)](https://www.codefactor.io/repository/github/tailuge/bot-o-tron) [![Open in Gitpod](https://img.shields.io/badge/Gitpod-Open%20in%20Gitpod-%230092CF.svg)](https://gitpod.io/#https://github.com/tailuge/bot-o-tron) 

This project creates a simple chess bot using javascript that connects to [lichess'](https://lichess.org) bot interface https://lichess.org/api#tag/Bot . This project can be hosted free on cloud providers such as [render.com](https://render.com). Play against this bot unrated now on lichess at [@bot-o-tron](https://lichess.org/@/bot-o-tron)


### Setup

- Get an [API token](https://lichess.org/account/oauth/token) from lichess.org and add it as an environment variable on your machine or cloud hosting provider.

```bash
$ nvm use v10.15.3
$ yarn install

# Linux
$ export API_TOKEN=xxxxxxxxxx

# Windows
$ setx API_TOKEN xxxxxxxxxx
```

### Run

The project runs as a express node server that connects to the lichess BOT account using the API_TOKEN

```bash
$ yarn start
```

### Local unit tests and code coverage

```bash
$ yarn test
```


To implement your chess bot you only need to create one class that implements the method:

```js
  getNextMove(moves) {
      return uciMove;
  }
```

Where moves is a list of moves so far in uci format e.g. `["e2e4", "b8c6", "f2f4"]`

See [`RandomPlayer`](src/bots/RandomPlayer.js) for minimal implementation using [chess.js](https://github.com/jhlywa/chess.js/blob/master/README.md)

### Free Cloud Hosting

If you register a free render.com account you can host a BOT like this one as is - just add your `API_TOKEN` to the environment property configuration.
This code auto deploys and is live at https://bot-o-tron.onrender.com/

[![Deploy to Render](https://render.com/images/deploy-to-render-button.svg)](https://render.com/deploy)

### Tounaments

Compare bots locally in a round-robin tournament 

```bash
$ yarn tournament

Results
[ { player: 'AntiPatzerPlayer    ', score: 32.5 },
  { player: 'PatzerPlayer        ', score: 23 },
  { player: 'RandomPlayer        ', score: 22.5 },
  { player: 'SwarmKingPlayer     ', score: 18 } ]
```
