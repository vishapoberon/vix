# vix

Vix is a simple, POSIX-shell-based project and build manager for [Vishap Oberon](https://vishap.oberon.am) projects.
It provides commands to create a new project skeleton, compile library modules, link and run your program, run tests, and produce release binaries.

## vix in action

[![asciicast](https://asciinema.org/a/723640.svg)](https://asciinema.org/a/723640)

## Installation

1. clone this repository
2. `sudo cp vix /usr/local/bin/vix`

## Usage

```
Usage: vix ...
  help
  version
  new PATH [--module MODULE] [--app APP]
  run
  build
  test
  release
```

```
vix new hello_world
```

## Directory Layout

```
hello_world/
  src/
    HelloWorld.Mod          ← library API
    HelloWorldMain.Mod      ← "main" program entry
  test/
    HelloWorldTest.Mod      ← test suite
  vipakfile                 ← project manifest
  README.md
  .gitignore
  .gitattributes
```

## vipakfile format

```
NAME      = hello_world
VERSION   = 0.1.0

AUTHOR    = 
LICENSE   = 

DEPS      = 

RUN       = ./HelloWorldMain
MAIN      = %projdir%/src/HelloWorldMain.Mod
BUILD     = %projdir%/src/HelloWorld.Mod

TEST_RUN  = ./HelloWorldTest
TEST_MAIN = %projdir%/test/HelloWorldTest.Mod
TEST      = 
```

- `%projdir%` is replaced at runtime with the project root directory.
- Semicolons (`;`) separate multiple entries, preserving order.

## TODO

- Integrate `vix` with `vipak` for dependency management
- Incremental builds
- Release tarballs, Dockerfiles and Jailerfiles
- Rewrite vix in Oberon
