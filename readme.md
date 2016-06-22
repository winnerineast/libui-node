# libui-node

> libui Node.js bindings.

[![Travis Build Status](https://img.shields.io/travis/parro-it/libui-node/master.svg)](http://travis-ci.org/parro-it/libui-node)
[![NPM module](https://img.shields.io/npm/v/libui-node.svg)](https://npmjs.org/package/libui-node)
[![NPM downloads](https://img.shields.io/npm/dt/libui-node.svg)](https://npmjs.org/package/libui-node)

[libui](https://github.com/andlabs/libui) is a simple and portable (but not inflexible) GUI library in C that uses the native GUI technologies of each platform it supports.

It is in early stage of development, but is evolving at great pace and is really awesome.

It could become an awesome, lightweight alternative to Electron to develop multiplatform GUI.

<p align="center">
<h2>Linux</h2>
<img src ="https://cloud.githubusercontent.com/assets/11197111/15990529/68e924f4-3095-11e6-8a13-b91678def555.png">
</p>

<center>
## OSX
![OSX](https://cloud.githubusercontent.com/assets/11197111/16003613/bf03b908-315d-11e6-9c67-850ace39ffc1.png)
</center>


# Supported platform

* Windows: Windows Vista SP2 with Platform Update or newer
* Unix: GTK+ 3.10 or newer
* Mac OS X: OS X 10.8 or newer

# Node version requirement

The project run on any node version > 0.12.

# Project status

* All current `libui` API, except for [these ones](https://github.com/parro-it/libui-node/issues?q=is%3Aissue+is%3Aopen+label%3A%22Missing+bind%22) are implemented.
* I'm developing on `linux`, so this is the preferred platform to test. OSX should work too, but it's not tested. Windows has yet to be configured in build scripts, but it will be supported in further releases.
* There are some tests developed, and they are passing in `Travis` thank you to @jjrv awesome work, both on OSX and on Linux, in Node > 0.12
* This is not yet battle-tested in a real app, but the control gallery example you saw in the screenshot above is fully working.

# Installation

We had published a first pre-release to npm.
You can now install `libui-node` as a simple dependency in your project:

```bash
npm install -S libui-node
```

`libui` prebuilt binaries are automatically downloaded after install.


# Examples

Some example in examples folder uses ES6 syntax. We will soon configure babel transpilation for them. Meanwhile, if you are testing the project on Node.js < 6, you can check `examples/core-api.js` that use Es5 syntax.

First, you have to clonse the GitHub repo and npm install it:

```bash
git clone https://github.com/parro-it/libui-node.git
npm install
```

Then, to run the control gallery example, type:

```bash
npm start
```

And for the core api, example, type:

```bash
npm run start-core
```


# Usage

Plase look in [examples folder](https://github.com/parro-it/libui-node/tree/master/examples).
We will write complete API documentation soon...


# Future directions of the project

## API

This binding is actually implementing low-level API straight to the `libui` ones.
We plan to add another level of API on top of it to simplify GUI building. You can get a taste of how they will be in [example utils.js file](https://github.com/parro-it/libui-node/blob/master/examples/utils.js).

This new API will support transpilation from JSX to further simplify GUI building.

These works will become in future the base for a React-Native like project.

# Contribution & design

* Each `libui` widget implementaion is written in it's own C++ file in `src` folder.
* Each widget is implemented in it's own C++ class, each class is a simple wrapper for related libui C functions.
* There is an header file called `src/ui-node.h` that contains all classes definitions.
* Widget events does not follow `node` convention: if you attach an handler to an event, previous one will be overwritten and never be called. This will be resolved on future high-level API repo, where each widget will be an `EventEmitter` instance.
* We build the project using the awesome [nbind](https://github.com/charto/nbind) tool, that automate the process of linking a straight C++ class to Node.js stuff...
* All the GUI code run in the node javascript main thread. You must call `libui.startLoop` to start the GUI event loop. It run one step at a time, you can see in [index.js](https://github.com/parro-it/libui-node/blob/master/index.js) how this is implemented.

## Useful NPM scripts

* test - run AVA tests && XO linting.
* start - start the control gallery example
* build - rebuild C++ sources

## Related projects

* [libui](https://github.com/andlabs/libui) - Simple and portable (but not inflexible) GUI library in C that uses the native GUI technologies of each platform it supports.
* [nbind](https://github.com/charto/nbind) - Magical headers that make your C++ library accessible from JavaScript

# Contributors


[![Andrea Parodi](https://avatars0.githubusercontent.com/u/11197111?s=130)](https://github.com/parro-it) | [![Juha Järvi](https://avatars3.githubusercontent.com/u/778781?s=130)](https://github.com/jjrv) | [![Chan Guan Hao](https://avatars1.githubusercontent.com/u/5748750?s=130)](https://github.com/mavenave)
---|---|---
[Andrea Parodi](https://github.com/parro-it) | [Juha Järvi](https://github.com/jjrv) | [Chan Guan Hao](https://github.com/mavenave)



# License

The MIT License (MIT)

Copyright (c) 2016 parro-it
