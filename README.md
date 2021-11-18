# Deprecated

❗ All zinit-packages have been migrated to https://github.com/zdharma-continuum/zinit-packages
You'll find the source for this here package in https://github.com/zdharma-continuum/zinit-packages/tree/HEAD/svn
# apache/subversion as a Zsh package

##### Homepage link: [apache/subversion](https://github.com/apache/subversion)

| **Package source:** | Source Tarball | Binary | Git | Node | Gem |
|:-------------------:|:--------------:|:------:|:---:|:----:|:---:|
| **Status:**         |    + <br> (default) |  -  | + | – |  –  |

[Zinit](https://github.com/zdharma-continuum/zinit) can use the NPM package registry
to automatically:

- get the plugin's Git repository OR release-package URL,
- get the list of the recommended ices for the plugin,
    - there can be multiple lists of ices,
    - the ice lists are stored in *profiles*; there's at least one profile, *default*,
    - the ices can be selectively overriden.

Example invocations that'll install
[apache/subversion](https://github.com/apache/subversion) either from the release archive
or from Git repository:

```zsh
# Download and install the APR dependency of Subversion
zinit pack for apr
# Download, build and install the latest Subversion source tarball
zinit pack for subversion
```

## Default Profile

Provides the Subversion revision control system by compiling and installing it
to the `$ZPFX` directory (`~/.zinit/polaris` by default). It uses the
[zinit-zsh/z-a-as-monitor](https://github.com/zinit-zsh/z-a-as-monitor) annex to
download the latest Subversion tarball.

The Zinit command executed will be equivalent to:

```zsh
zi as"null|monitor" dlink"https://.*/subversion-%VERSION%.tar.bz2" \
    atclone'zpextract --move --auto; print -P \\n%F{75}Building Subversion...\\n%f; ./configure \
        --prefix="$ZPFX" --with-apr='$ZPFX' >/dev/null && make >/dev/null && print -P \
        \\n%F{75}Installing Subversion to $ZPFX...\\n%f && make install >/dev/null && print -P \
        \\n%F{34}Installation of Subversion succeeded.%f || \
        print -P \\n%F{160}Installation of Subversion failed.%f' \
    atpull'%atclone' for \
        https://subversion.apache.org/download.cgi
```

<!-- vim:set ft=markdown tw=80 fo+=an1 autoindent: -->
