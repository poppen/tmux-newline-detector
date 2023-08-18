tmux newline detector
=====================

This [tpm](https://github.com/tmux-plugins/tpm) plugin detects newline in tmux buffer (or clipboard if you use [reattach-to-user-namespace](https://github.com/ChrisJohnsen/tmux-MacOSX-pasteboard) on macOS or [win32yank](https://github.com/equalsraf/win32yank) on WSL in Windows), and asks for you whether or not pasting it to terminal with **kindness**. Also, add **peek** key binding to show what is in tmux buffer.

What is **kindess**? If your buffer is only one sentence and includes newline, this plugin removes the newline! But nothing to do if several sentences buffered in tmux.

## Requirements

1. [tmux](https://github.com/tmux/tmux)
2. [tpm](https://github.com/tmux-plugins/tpm)
3. [reattach-to-user-namespace](https://github.com/ChrisJohnsen/tmux-MacOSX-pasteboard) (optional)
4. [win32yank](https://github.com/equalsraf/win32yank) (optional)

## Install

Add the following lines to your `~/.tmux.conf`

```bash
set-option -g @plugin knakayama/tmux-newline-detector
```

then, press `Prefix + I` in tmux session.

## Usage

Default peek key binding is `Prefix + P`. If you change this key binding, set the following line to your `~/.tmux.conf`.

```bash
set-option -g @peek 'x' # or your favorite key binding
```

Default paste key binding is `Prefix + ]`. If you change this key binding, set the following line to your `~/.tmux.conf`.

```bash
set-option -g @paste 'X' # or your favorite key binding
```

This will manage the plugin bindings for you, but if you need to do something more complex, like pass arguments, you'll need to do that yourself:

```bash
bind-key X run-shell "~/.tmux/plugins/tmux-newline-detector/scripts/paste.sh -p"
bind-key x choose-buffer "run-shell \"~/.tmux/plugins/tmux-newline-detector/scripts/paste.sh -b '%%'\""
```

Note that due to the way the scripts process their arguments,
arguments with spaces in them are not likely to work.

## License

MIT

## Author

[knakayama](https://github.com/knakayama)
