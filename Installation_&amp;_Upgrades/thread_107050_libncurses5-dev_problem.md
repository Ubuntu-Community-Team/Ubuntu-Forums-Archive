---
title: "libncurses5-dev problem"
date: 2005-12-22
forum: Installation &amp; Upgrades
---

### Post by Reggie on 2005-12-22
When trying to install libncurses5-dev I get the following error:

> 
Unpacking libncurses5-dev (from .../libncurses5-dev_5.4-4_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libncurses5-dev_5.4-4_i386.deb (--unpack):
 trying to overwrite `/usr/include/curses.h', which is also in package ncurses-devel
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libncurses5-dev_5.4-4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


What can I do to fix this ??

---

### Post by pauljwells on 2005-12-22
You need to be a bit careful - you've got yourself a dependency conflict and 'fixing' it might break something else. I would try to find out what is depending on the installed file (if you mark it for removal in synaptic, it will tell you what other packages will be removed also - these are the ones that depend on it). Write these down so that if you ever get an error when you run them you know what it might be. (I'd save the list in a text file along with a copy of the installed file - see next...)

Assuming that you still want to go ahead and overwrite, make a copy of the installed file (in case it all goes wrong!) and then in a terminal, install the package using sudo dpkg. I forget the exact syntax but you need to set the flags for forced overwrite. It's all in man dpkg - I had to do it a few weeks ago and it was fairly easy to follow. I'm not on my Ubuntu machine at the moment or I'd take a quick look myself.

Try searching these forums for help on dpkg and you might find some more expert opinions than mine.

---

