---
title: "Ebcam driver module not compile in Feisty"
date: 2006-12-13
forum: Hardware &amp; Laptops
---

### Post by macozz on 2006-12-13
Hi all,
I try to compile the driver module for the Sunplus Felxcam 100 (spca5xx) in a Feisty installation (upgraded from Edgy). All the requirements are installed and I follow other suggestions found in several posts, however I have not succeed yet. This is the error output after make:
make -C /lib/modules/`uname -r`/build SUBDIRS=/usr/src/gspcav1-20060925 CC=gcc-3.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.19-7-generic'
  CC [M]  /usr/src/gspcav1-20060925/gspca_core.o
/usr/src/gspcav1-20060925/gspca_core.c:36:26: linux/config.h: No such file or directory
/usr/src/gspcav1-20060925/gspca_core.c: In function `gspca_init_isoc':
/usr/src/gspcav1-20060925/gspca_core.c:1035: warning: assignment from incompatible pointer type
make[2]: *** [/usr/src/gspcav1-20060925/gspca_core.o] Error 1
make[1]: *** [_module_/usr/src/gspcav1-20060925] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.19-7-generic'
make: *** [default] Error 2

....
I cannot figure out what is going on!

I Dapper the module was included in the kernel modules shipped with the distro, but it seems that disapear in Edgy and Feisty, anybody know why?

Thaks!

---

