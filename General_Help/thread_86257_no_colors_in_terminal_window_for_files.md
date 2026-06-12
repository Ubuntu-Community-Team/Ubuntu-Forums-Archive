---
title: "no colors in terminal window for files"
date: 2005-11-04
forum: General Help
---

### Post by wazoo on 2005-11-04
Didn't Ubuntu used to show file info in colors? That is, there was one color for directories, one for executables, etc. Mine doesn't do that anymore, because I accidentally blew away some ".gnome" files, I think. How do I get this feature back?

---

### Post by kroiz on 2005-11-04
I got this in .bashrc
```
# enable color support of ls and also add handy aliases
if [ "$TERM" != "dumb" ]; then
    eval "`dircolors -b`"
    alias ls='ls --color=auto'
fi

```

I think this does the coloring for ls.
try it out.

---

### Post by wazoo on 2005-12-19
That's it! Thank you!

---

