---
title: "Trouble installing omnibook kernel module"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by Nalroff on 2009-10-17
I've downloaded the source, got everything I need (I think), and when I run "make" it spits this stuff out, and I don't quite understand what it all means.

```

user@user-laptop:/usr/src/modules/omnibook$ sudo make
PWD=/usr/src/modules/omnibook
make -C /lib/modules/2.6.28-15-generic/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [omnibook.ko] Error 2

```

Any ideas?

---

### Post by Nalroff on 2009-10-17
bump?

---

