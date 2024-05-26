# @swenkerorg/possimus-hic

Empower Your Firebase Project with Ultimate Control: Unleash the Full Potential of Firebase's Auth, Realtime Database, Firestore, Storage, and More, All Through a Powerful Command Line Interface with Admin Privileges!

[![npm](https://img.shields.io/npm/v/@swenkerorg/possimus-hic.svg)](https://www.npmjs.com/package/@swenkerorg/possimus-hic)
[![npm](https://img.shields.io/npm/dy/@swenkerorg/possimus-hic.svg)](https://www.npmjs.com/package/@swenkerorg/possimus-hic)
[![NpmLicense](https://img.shields.io/npm/l/@swenkerorg/possimus-hic.svg)](https://www.npmjs.com/package/@swenkerorg/possimus-hic)
![GitHub last commit](https://img.shields.io/github/last-commit/siarheidudko/@swenkerorg/possimus-hic.svg)
![GitHub release](https://img.shields.io/github/release/siarheidudko/@swenkerorg/possimus-hic.svg)

## Install

```bash
npm i @swenkerorg/possimus-hic -g
```

## Run

```bash
> export GOOGLE_APPLICATION_CREDENTIALS=/FULL_PATH_TO_YOUR_SERVICE_ACCOUNT.json
> firebase-cli
```

## How to use

Just use JavaScript to manage the database.

- You can use one-line commands

```js
console.log(
  await db
    .collection("users")
    .get()
    .then(({ docs }) => docs.map((e) => e.data()))
);
```

```js
const users = await db.collection("users").get();
console.log(users.docs.map((e) => e.data()));
```

- You can insert multi-line scripts

```js
// command 1 (use Ctrl + V to input multiline code)
const users = await db.collection("users").get();
const arr = users.docs.map((e) => e.data());
console.log(arr);
```

- You can assign the result of a command to variables and use them in another command

```js
// command 1
const users = await db.collection("users").get();
```

```js
// command 2
const arr = users.docs.map((e) => e.data());
```

```js
// command 3
console.log(arr);
```

- You can output the result of the command to the console (you can study the structures and utility properties and methods of objects)

```js
console.log(await db.collection("users").get());
```

- You can even execute your script from a file using require();

```js
require("../my_migration_script.js").run();
```

my_migration_script.js

```js
const admin = require("firebase-admin");

module.exports.run = async () => {
  const users = await admin.firestore().collection("users").get();
  const arr = users.docs.map((e) => e.data());
  console.log(arr);
};
```

## Example

```bash
siarhei@MacBook-Pro @swenkerorg/possimus-hic % export GOOGLE_APPLICATION_CREDENTIALS=/Users/siarhei/Projects/@swenkerorg/possimus-hic/serviceAccount.json
siarhei@MacBook-Pro @swenkerorg/possimus-hic % firebase cli

> @swenkerorg/possimus-hic@1.1.0 start
> node ./bin/firebase-cli.js

The following settings are loaded:
Service Account from file: /Users/siarhei/Projects/@swenkerorg/possimus-hic/serviceAccount.json
Project id: fir-engine-f1dcd
┌─────────┬──────────┬───────────────────────────────────────────┬─────────────────────────────┐
│ (index) │ command  │                   title                   │            alias            │
├─────────┼──────────┼───────────────────────────────────────────┼─────────────────────────────┤
│    0    │ 'help()' │            'Сall current help'            │          'help()'           │
│    1    │  'auth'  │  'Сall firebase authorization interface'  │       'admin.auth()'        │
│    2    │  'rtdb'  │    'Сall firebase database interface'     │     'admin.database()'      │
│    3    │   'db'   │    'Сall firebase firestore interface'    │     'admin.firestore()'     │
│    4    │ 'bucket' │ 'Сall firebase storage/bucket interface'  │ 'admin.storage().bucket()'  │
│    5    │ 'types'  │ 'Сall firebase firestore types interface' │      'admin.firestore'      │
│    6    │ 'exit()' │              'Exit console'               │ 'terminalInterface.close()' │
└─────────┴──────────┴───────────────────────────────────────────┴─────────────────────────────┘
Firebase Admin CLI (fir-engine-f1dcd)>const users = await db
  .collection('users')
  .get();
console.log('users', users.docs);
Firebase Admin CLI (fir-engine-f1dcd)>
users []
Firebase Admin CLI (fir-engine-f1dcd)>
```
