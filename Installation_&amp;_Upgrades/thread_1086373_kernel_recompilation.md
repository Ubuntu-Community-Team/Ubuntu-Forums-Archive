---
title: "kernel recompilation"
date: 2009-03-03
forum: Installation &amp; Upgrades
---

### Post by lam_tezu on 2009-03-03
the following error notification comes while recompiling kernel

#
# configuration written to .config
#
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
/usr/bin/make EXTRAVERSION=.3-custom   ARCH=i386 prepare
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-22-generic'
scripts/kconfig/conf -s arch/x86/Kconfig
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-22-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[2]: *** No rule to make target `arch/x86/kernel/asm-offsets.c',
needed by `arch/x86/kernel/asm-offsets.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-22-generic'
make: *** [debian/stamp-kernel-conf] Error 2
root@lamjing-desktop:/usr/src/linux#


what should be done for this. presently m using ubuntu with kernel
version-2.6.24. and m recompiling it again with the tar file that is
already there in the /usr/src/ directory.

[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)

m followint the steps given in the above link.

---

### Post by lam_tezu on 2009-03-05
its working now...

---

