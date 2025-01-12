<!-- panvimdoc-ignore-
start
 -->

<img src=".github/logo.png" alt="Logo" align="right" width="128"/>

# nvimcord

A Discord Rich Presence plugin for Neovim written in Lua.

<!-- panvimdoc-ignore-end -->

## The provided snippet is a Markdown header for a README file. Here is the snippet:

```markdown
# website
```

### Analysis
1. **Header Clarity**: The current header "website" is quite generic. It doesn’t provide specific information about the project.
2. **Documentation Completeness**: A typical README should include sections like project description, installation instructions, usage, contributing guidelines, and license information.

### Recommendations
1. **Improve Header Specificity**: Change the header to something more descriptive about the project.
2. **Add Sections**: Include additional sections to make the README more informative for users and contributors.

### Improved Code Example

```markdown
# My Awesome Website

[![Release package](https://github.com/mdn/browser-compat-data/actions/workflows/release.yml/badge.svg?branch=revert-21461-dependabot%2Fgithub_actions%2Factions%2Flabeler-5&event=watch)](https://github.com/mdn/browser-compat-data/actions/workflows/release.yml)## Description
A brief description of what the project is about.

## Installation
Instructions on how to set up the project locally.

## Usage
How to use the project after it is set up.

## Contributing
Guidelines for contributing to the project.

## License
Information about the license under which the project is distributed.
```

This structure provides a clear and comprehensive overview of the project, making it easier for others to understand, use, and contribute to it.

### lazy.nvim

```lua
{
  'ObserverOfTime/nvimcord',
  opts = {
    ...
  }
}
```

###
  (# pckr.nvim

```lua
{
  'ObserverOfTime/nvimcord',
  config = function()
    require('nvimcord').setup {
      ...
    }
  end
}
```

## Configuration

These are the default values:

```lua
-- Start the RPC manually (boolean)
autostart = false

-- Set the client ID (string)
client_id = '954365489214291979'

-- Update workspace on chdir (boolean)
dynamic_workspace = false

-- Use the filetype as the large icon (boolean)
large_file_icon = true

-- Set the log level (vim.log.levels.*)
log_level = vim.log.levels.INFO

-- Get the workspace name (function|string)
workspace_name = function()
  return --[[git root or cwd basename]]
end

-- Get the workspace URL (function|string)
workspace_url = function()
  return --[[git remote URL]]
end
```

Options can also be configured using Vim variables.

This can be useful when using [exrc] or a project plugin.

```vim
let g:nvimcord#autostart = v:false
let g:nvimcord#client_id = '954365489214291979'
let g:nvimcord#dynamic_workspace = v:false
let g:nvimcord#large_file_icon = v:true
let g:nvimcord#log_level = 2
" NOTE: these can only be defined as strings
let g:nvimcord#workspace_name = ''
let g:nvimcord#workspace_url = ''
```

[exrc]: https://neovim.io/doc/user/starting.html#exrc

### Filetypes

```lua
local fts = require 'nvimcord.filetypes'

-- NOTE: the asset can also be an image URL

-- override options
fts.filetype['vim'].name = 'Vim Script'
fts.filetype['vim'].asset = 'neovim'

-- new filetype
fts.filetype['teal'] = {name = 'Teal', asset = 'lua'}

-- new pattern
fts.pattern['^%.gitkeep$'] = {name = 'git keep', asset = 'git'}

-- ignore filetype
fts.ignore.filetype['vim'] = true

-- ignore filename
fts.ignore.filename['init.vim'] = true
```

## Commands

#### :NvimcordUpdate

Start or update the rich presence.

#### :NvimcordStop

Stop the rich presence.

#### :NvimcordFiletypes

List the supported filetypes.

#### :NvimcordAssets

List the supported assets.

## TODO

* [x] Ignore by filename
* [ ] Cache filename patterns
* [x] Detect workspace through git
* [x] Warn when pipe doesn't exist
* [ ] Set idle status after some time

## Assets

The assets are available [here][disroot].

### Sources

- [file-icons/icons](https://github.com/file-icons/icons)
- [file-icons/DevOpicons](https://github.com/file-icons/DevOpicons)
- [file-icons/MFixx](https://github.com/file-icons/MFixx)
- [primer/octicons](https://github.com/primer/octicons)

### Palette

The icons use the basic colours from [file-icons/atom][colours].

<!-- panvimdoc-ignore-start -->

- ![#ac4142](https://dummyimage.com/12x12/ac4142&text=+ "#ac4142") red<br>
- ![#90a959](https://dummyimage.com/12x12/90a959&text=+ "#90a959") green<br>
- ![#f4bf75](https://dummyimage.com/12x12/f4bf75&text=+ "#f4bf75") yellow<br>
- ![#6a9fb5](https://dummyimage.com/12x12/6a9fb5&text=+ "#6a9fb5") blue<br>
- ![#8f5536](https://dummyimage.com/12x12/8f5536&text=+ "#8f5536") maroon<br>
- ![#aa759f](https://dummyimage.com/12x12/aa759f&text=+ "#aa759f") purple<br>
- ![#d28445](https://dummyimage.com/12x12/d28445&text=+ "#d28445") orange<br>
- ![#75b5aa](https://dummyimage.com/12x12/75b5aa&text=+ "#75b5aa") cyan<br>
- ![#ff00cc](https://dummyimage.com/12x12/ff00cc&text=+ "#ff00cc") pink<br>
- ![#7f7f7f](https://dummyimage.com/12x12/7f7f7f&text=+ "#7f7f7f") grey<br>

<!-- panvimdoc-ignore-end -->

[disroot]: https://cloud.disroot.org/s/3HCpppopkrcR6iK
[colours]: https://github.com/file-icons/atom/blob/master/styles/colours.less#L10-L19

## Alternatives

- [amiralies/coc-discord] (TypeScript)
- [andweeb/presence.nvim] (Lua)
- [aurieh/discord.nvim] (Remote Python)
  - [or my own fork][ObserverOfTime/discord.nvim]
- [Cyuria/discord.nvim] (Lua + C++)
- [GabeFrahm/vim-presence] (Python)
- [goopey7/vdrpc] (VimL + C)
- [IogaMaster/neocord] (Lua)
- [LeonardSSH/coc-discord-rpc] (TypeScript)
- [lpturmel/discord.nvim] (Lua + Rust)
- [SamJakob/coc-discord-presence] (TypeScript)
- [sardonicism-04/nvim-rich-presence] (VimL + Rust)
- [Stoozy/vimcord] Python
- [TCL100K/vim-discord-rpc] (Python)
- [vbe0201/vimdiscord] (Python)
- [vyfor/cord.nvim] (Lua + Rust)

[amiralies/coc-discord]: https://github.com/amiralies/coc-discord
[andweeb/presence.nvim]: https://github.com/andweeb/presence.nvim
[aurieh/discord.nvim]: https://github.com/aurieh/discord.nvim
[Cyuria/discord.nvim]: https://github.com/Cyuria/discord.nvim
[GabeFrahm/vim-presence]: https://github.com/GabeFrahm/vim-presence
[goopey7/vdrpc]: https://github.com/goopey7/vdrpc
[IogaMaster/neocord]: https://github.com/IogaMaster/neocord
[LeonardSSH/coc-discord-rpc]: https://github.com/LeonardSSH/coc-discord-rpc
[lpturmel/discord.nvim]: https://github.com/lpturmel/discord.nvim
[ObserverOfTime/discord.nvim]: https://github.com/ObserverOfTime/discord.nvim
[SamJakob/coc-discord-presence]: https://github.com/SamJakob/coc-discord-presence
[sardonicism-04/nvim-rich-presence]: https://github.com/sardonicism-04/nvim-rich-presence
[Stoozy/vimcord]: https://github.com/Stoozy/vimcord
[TCL100K/vim-discord-rpc]: https://github.com/TCL100K/vim-discord-rpc
[vbe0201/vimdiscord]: https://github.com/vbe0201/vimdiscord
[vyfor/cord.nvim]: https://github.com/vyfor/cord.nvim
