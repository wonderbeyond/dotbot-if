[dotbot_repo]: https://github.com/anishathalye/dotbot
[dotbot_ifplatform]: https://github.com/ssbanerje/dotbot-ifplatform
[self_repo]: https://github.com/wonderbeyond/dotbot-if.git

## Dotbot `if` Plugin

Conditional execution of [Dotbot][dotbot_repo] directives based on a shell command's exit status (success or failure). Inspired by [dotbot-ifplatform][dotbot_ifplatform].

## Prerequisites

This plugin requires [Dotbot][dotbot_repo] to be installed.

## Installation

1. Run `git submodule add https://github.com/wonderbeyond/dotbot-if.git`
2. Run `git submodule update --init --recursive`
3. Pass in the CLI argument `-p dotbot-if/if.py` when calling the `dotbot` executable.

## Usage

Add the `if..cond..met..unmet` structure in the `dotbot` YAML file
to conditionally execute any other directives. For examples:

### The `if..else` equivalent

You can omit any `met` or `unmet` part if you want do nothing at that state.

```yaml
- if:
    cond: 'python -V | grep -Eq "Python\s+3\."'
    met:
    - shell:
      - echo Found Python 3.
    unmet:
    - shell:
      - echo Python3 not found!
```

### Multiple parameter groups for single `if`

Can be the `switch/match..case` equivalent.

```yaml
- if:
  - cond: 'command -v apt-get'
    met:
    - apt:
      - jq
  - cond: 'command -v brew'
    met:
    - brew:
      - jq
```
