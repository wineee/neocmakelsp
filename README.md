# CMake lsp based on Tower and treesitter

[![Crates.io](https://img.shields.io/crates/v/neocmakelsp.svg)](https://crates.io/crates/neocmakelsp)

It is a CMake lsp based on tower-lsp and treesitter 

## Install

```
cargo install neocmakelsp
```

## Setup

```lua
local configs = require("lspconfig.configs")
local nvim_lsp = require("lspconfig")
if not configs.neocmake then
    configs.neocmake = {
        default_config = {
            --cmd = { "./target/debug/qmllsp" },
            cmd = { "./target/debug/neocmakelsp" },
            filetypes = { "cmake" },
            root_dir = function(fname)
                return nvim_lsp.util.find_git_ancestor(fname)
            end,
            on_attach = on_attach
        }
    }
    nvim_lsp.neocmake.setup({})
end
```


## Features

* complete
* symbol\_provider
* On hover

## TODO

* GO TO Definitation
* Undefined function check

## Show

### Complete and symbol support
![Show](https://raw.githubusercontent.com/Decodetalkers/utils/master/cmakelsp/demo.gif)

### OnHover
![Show](https://raw.githubusercontent.com/Decodetalkers/utils/master/cmakelsp/onhover.jpg)

