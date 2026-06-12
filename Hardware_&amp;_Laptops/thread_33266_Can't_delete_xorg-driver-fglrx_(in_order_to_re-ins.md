---
title: "Can't delete xorg-driver-fglrx (in order to re-install driver)"
date: 2005-05-10
forum: Hardware &amp; Laptops
---

### Post by dolny on 2005-05-10
```
Deleting xorg-driver-fglrx ...
dpkg-divert: rename involves overwriting `/usr/X11R6/lib/libGL.so.1.2' with
  different file `/usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa', not allowed
Error while processing:
 xorg-driver-fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
dolny@milkshake:~$ dpkg-divert --package fglrx --remove /usr/X11R6/lib/libGL.so.1.2
dpkg-divert: mismatch on package
  when removing `diversion of /usr/X11R6/lib/libGL.so.1.2 by fglrx'
  found `diversion of /usr/X11R6/lib/libGL.so.1.2 to /usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
```

I use Hoary Hedgehog 5.04 but I tried this tutorial **(not for Hoary)** which probably messed my files:
[http://www.ubuntuforums.org/showthread.php?t=5356](http://www.ubuntuforums.org/showthread.php?t=5356)

Now I want to delete everything and start over but I can't delete it. Can you help me?

I'm using Kubuntu HH 5.04. (I want to install 3d acceleration for my ATI Radeon 9600 - 3rd day of trying) ... :(

---

### Post by manadskort on 2005-08-03
dpkg-divert --package fglrx --remove /usr/X11R6/lib/libGL.so.1.2

---

