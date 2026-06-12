---
title: "Liferea does not start; HTML plugin error"
date: 2008-08-04
forum: General Help
---

### Post by tak1150 on 2008-08-04
Hi,

All of a sudden, today, I cannot start Liferea! I've always been able to!
Other than installing to see what "[Ultamatix]("http://ultamatix.com/")" looks like (I have not installed anything from Ultamatix), and installing the good ol' updates, I really haven't done anything to my machine lately.

Here's what I get from terminal
```
user@computer:~$ liferea --debug-plugins
PLUGINS: Scanning for plugins (/usr/lib/liferea):
PLUGINS: -> libnotify notification (liblinotiflibnotify.so, type=3)
PLUGINS: -> LUA Scripting Support Plugin (libliscrlua.so, type=4)
PLUGINS: Cannot open /usr/lib/liferea/liblihtmlm.so (libgtkembedmoz.so: cannot open shared object file: No such file or directory)!
!
** ERROR **: Sorry, I was not able to load any installed browser plugin! Try the --debug-plugins option to get debug information!
aborting...
Aborted
```

Any help? Thank you!

PS I copied "libgtkembedmoz.so" from /usr/lib/thunderbird/ to /usr/lib/liferea/ and it didn't do anything :(

---

