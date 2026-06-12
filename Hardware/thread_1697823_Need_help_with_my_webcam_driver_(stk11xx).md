---
title: "Need help with my webcam driver (stk11xx)"
date: 2011-03-01
forum: Hardware
---

### Post by snufk1n on 2011-03-01
> ~/Webcam/SVN/syntekdriver/trunk/driver$ sudo make -f Makefile.standalone 
make -C /lib/modules/2.6.32-28-generic/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-28-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
[B]make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-28-generic'
make: *** [driver] Error 2[/B]I need help compiling the drivers for my webcamera. I've successfully compiled it and used it several times but not since I got the latest version of the kernel. Now I can't even use an old kernel and compile it as I've done so many times before. 

What do I have to do to get it to work? I've tried reinstalling the kernel-headers as suggested on some other site but it's still not working.

---

