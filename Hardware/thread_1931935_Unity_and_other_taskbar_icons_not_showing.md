---
title: "Unity and other taskbar icons not showing"
date: 2012-02-26
forum: Hardware
---

### Post by parth.s on 2012-02-26
I am using 11.10 on a dual boot machine, and recently I was playing around with ccsm(compiz manager). To enable the desktop cube effect, I disabled the Desktop wall plugin. A popup came up, i dont remember exactly but it asked to disable all plugins, and I selected OK. My taskbar vanished and realizing this I enabled the plugin again.

Now the unity and all the options from my taskbar are gone! What do I do? Everything including the system settings and the network connections is missing..

---

### Post by ajgreeny on 2012-02-26
To reset compiz and unity run these two commands in terminal.  If you can not open a terminal in the usual way, try Ctrl+Alt+T.
```
gconftool-2 --recursive-unset /apps/compiz
unity --reset
```

---

### Post by parth.s on 2012-02-26
Let me try it out and will let you know asap...
thanks

---

### Post by parth.s on 2012-02-28
It worked! But I kept getting a few errors in the terminal window, one of which was cannot find the 'pixmap'..so I had to interrupt it and restart.
Thanks a lot!

---

