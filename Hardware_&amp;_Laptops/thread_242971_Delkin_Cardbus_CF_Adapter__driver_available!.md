---
title: "Delkin Cardbus CF Adapter:  driver available!"
date: 2006-08-24
forum: Hardware &amp; Laptops
---

### Post by mlord on 2006-08-24
I have updated my driver for the Delkin Cardbus CompactFlash adapter card --> it can now build as a standalone kernel module, which means it is much easier to use.  No need to rebuild or reinstall your Ubuntu kernel in order to use this driver now.

I'm posting here just so people can find the darned thing with google or the forum search.

The driver is available here:  [http://rtr.ca/](http://rtr.ca/)

At some point, I will re-implement it as a pure Linux-2.6 libata driver and get it included in the standard kernel.org tree.  Later, much.

Cheers

Mark

---

### Post by Frogzoo on 2008-01-15
Fails to build on Gutsy:

make -C /lib/modules/`uname -r`/build M=`pwd` modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  ~/delkin_cb-2.6.15+/delkin_cb.o
~/delkin_cb-2.6.15+/delkin_cb.c:21:26: error: linux/config.h: No such file or directory
~/delkin_cb-2.6.15+/delkin_cb.c: In function ‘delkin_cb_probe’:
~/delkin_cb-2.6.15+/delkin_cb.c:83: warning: passing argument 2 of ‘ide_register_hw_with_fixup’ makes integer from pointer without a cast
~/delkin_cb-2.6.15+/delkin_cb.c:83: warning: passing argument 3 of ‘ide_register_hw_with_fixup’ from incompatible pointer type
~/delkin_cb-2.6.15+/delkin_cb.c:83: error: too few arguments to function ‘ide_register_hw_with_fixup’
~/delkin_cb-2.6.15+/delkin_cb.c: In function ‘delkin_cb_init’:
~/delkin_cb-2.6.15+/delkin_cb.c:125: warning: implicit declaration of function ‘pci_module_init’
make[2]: *** [~/delkin_cb-2.6.15+/delkin_cb.o] Error 1
make[1]: *** [_module_~/delkin_cb-2.6.15+] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [all] Error 2

---

