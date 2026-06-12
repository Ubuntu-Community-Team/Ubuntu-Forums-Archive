---
title: "PKG_CONFIG_PATH error"
date: 2008-10-10
forum: General Help
---

### Post by RRLangly on 2008-10-10
I'm trying to build an app on the eeepc which has ubuntu installed via a usb drive and I ported my small app and getting the following error.

```

make[1]: Entering directory `/home/me/Projects/myApp'
gcc -I. -Wall -O1 -g -D_REENTRANT -I/usr/local/include -DLINUX -fPIC `pkg-config --cflags glib-2.0`   -c -o resval.o resval.c
Package glib-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `glib-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'glib-2.0' found

```

Can anyone tell me what I need there?

---

### Post by geirha on 2008-10-10
When you get a message like that, you usually need a -dev package. ```
aptitude search glib.*-dev
```
I would guess [libglib2.0-dev](apt://libglib2.0-dev) is the package you need to install

---

