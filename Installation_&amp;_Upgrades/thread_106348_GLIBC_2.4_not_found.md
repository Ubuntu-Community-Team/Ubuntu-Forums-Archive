---
title: "GLIBC_2.4 not found"
date: 2005-12-20
forum: Installation &amp; Upgrades
---

### Post by thoriumbr on 2005-12-20
Hi everyone,
I installed AT&T Network client in my Ubuntu 5.10, but it simply not runs. And when I tryed to run apt-get, I get this message:
/usr/lib/tsl/comv/i686/libc.so.6: version GLIBC_2.4 not found (required by /usr/lib/libstdc++.so.6

I uninstalled libc-compat (something like this), manually installed my old versions of libc and stdlib, but still not running gnome, apt-get, synaptic...
What can I do?

I am thinking in reinstalling everything, but not like the idea...

---

### Post by analalovic on 2008-07-08
You can find glibc-package with additional documentation at

[http://packages.ubuntu.com/search?keywords=glibc&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=glibc&searchon=names&suite=all&section=all)
 
It worked for me ...

---

