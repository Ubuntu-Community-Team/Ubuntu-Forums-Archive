---
title: "latest 13.04 update broke nvidia drivers"
date: 2013-04-09
forum: Hardware
---

### Post by darkenedday on 2013-04-09
After installing the updates from the software center today, I restarted to find x broken. I then tried to run startx and got the following.

Libkmod: ERROR ../libkmod/libkmod-module.c:791 kmod_module_insert_module: could not find module by name='nvidia_310'
ERROR: could not insert 'nvidia_310' : function not implemented

---

### Post by Yellow Pasque on 2013-04-09
It's happening to everyone else too, so just hold tight: [https://bugs.launchpad.net/bugs/576648](https://bugs.launchpad.net/bugs/576648)

---

### Post by darkenedday on 2013-04-10
alright good to know it's not something I did, will just keep trying to find a fix.

---

