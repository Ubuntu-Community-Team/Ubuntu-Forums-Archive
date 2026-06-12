---
title: "How do i add a C/C++ library?"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by lurikeen on 2009-04-11
I'm trying to get curses.h and ncurses.h, but I have no idea how. Any help?

---

### Post by ve4cib on 2009-04-11
Have you installed the libncurses development package?

```
sudo apt-get install libncurses5-dev
```

---

### Post by lurikeen on 2009-04-11
Yep, I get this:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
libncurses5-dev is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
  linux-image-2.6.27-3-rt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

Know what to make of this?

---

### Post by ve4cib on 2009-04-11
Nothing exciting about that output.  All it's saying is that you have the package installed and that you've got a few left-over dependencies from an old upgrade kicking around.

Could you please post the output of

```
locate curses.h
```

You should get

```
/usr/include/curses.h
/usr/include/ncurses.h
```
(and maybe some other lines of output, but those are the important ones).

Provided those are there then the problem is most likely with your code and/or your Makefile.

---

