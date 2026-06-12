---
title: "Using both cores to compile"
date: 2007-04-20
forum: Hardware &amp; Laptops
---

### Post by Aetherius on 2007-04-20
Just wondering if anyone could tell me how to get make to use both cores of CPU?

Would really help me out.

---

### Post by igknighted on 2007-04-20
> **Aetherius said:**
> Just wondering if anyone could tell me how to get make to use both cores of CPU?

Would really help me out.

you need to add a -j2 option to the compiler instructions.  In gentoo there is a nice file /etc/make.conf, I'm not sure how to enable it locally in Ubuntu though.

EDIT: what is it you are trying to compile?

---

### Post by yabbadabbadont on 2007-04-20
Actually, he should probably use "-j3".  The recommended "j" option is "number of cores plus one".  After you have run the ./configure and are ready for the make command, just append the "-j3" option.  Example:
```
./configure
make -j3
make install

```
Note that this was just a generic example.

---

### Post by Aetherius on 2007-04-23
thanks for the tips, not trying to compile anything in particular, just i often do alot of compiling and when i do i tend to not do anything else.....compilation-anxiety :P so i see it as wasteful only using one core

---

