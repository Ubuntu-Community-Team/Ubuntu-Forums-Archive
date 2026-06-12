---
title: "X suddenly unresponsive when laptop allowed to idle"
date: 2008-07-27
forum: General Help
---

### Post by everdred on 2008-07-27
I've experienced this problem twice this evening with a months-old installation of Hardy... here's what happened: I left my laptop alone for a while and returned to find it unresponsive, except for the mouse cursor (which can still be moved).

I'm unable to switch to a full-screen terminal to figure out what's wrong, but I was able to ssh in and have a look at the running processes. I found the following one maxing out one of my two CPU cores:

```
/usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -noliste
```

Does anyone have an idea of what's going on, or what else information I should provide? 

Many thanks in advance.

---

### Post by everdred on 2008-07-27
Might be good to note that I have the "Blank Screen" screensaver set (so it's not like there's something that should be eating up CPU) and the second time I saw this happen, the screen had not even been blanked.

---

