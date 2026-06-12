---
title: "Quantis installation about kernel configuration invalid"
date: 2007-05-23
forum: Hardware &amp; Laptops
---

### Post by ziruu on 2007-05-23
i install a new hardware call quantis random number generator 
i followed all the instruction and when i type make 
this error pop up about kernel configuration invalid
i very new to ubuntu 
and right now i dont have any idea what to do next
PLEASE HELP ME
:(:(:(:(:(
> 
root@sapura-desktop:/Quantis-PCI/src/linux# make
for i in driver lib qrng ; do cd $i && (make all || exit ) && cd ..; done
make[1]: Entering directory `/Quantis-PCI/src/linux/driver'
make -C /usr/src/linux M=/Quantis-PCI/src/linux/driver V=1 modules
make[2]: Entering directory `/usr/src/linux-source-2.6.20'
test -e include/linux/autoconf.h -a -e include/config/auto.conf || (           \
        echo;                                                           \
        echo "  ERROR: Kernel configuration is invalid.";               \
        echo "         include/linux/autoconf.h or include/config/auto.conf are missing.";      \
        echo "         Run 'make oldconfig && make prepare' on kernel src to fix it.";  \
        echo;                                                           \
        /bin/false)
mkdir -p /Quantis-PCI/src/linux/driver/.tmp_versions
rm -f /Quantis-PCI/src/linux/driver/.tmp_versions/*

  WARNING: Symbol version dump /usr/src/linux-source-2.6.20/Module.symvers
           is missing; modules will have no dependencies and modversions.

make -f scripts/Makefile.build obj=/Quantis-PCI/src/linux/driver
  Building modules, stage 2.
make -f /usr/src/linux-source-2.6.20/scripts/Makefile.modpost
  scripts/mod/modpost -m -a -i /usr/src/linux-source-2.6.20/Module.symvers -I /Quantis-PCI/src/linux/driver/Module.symvers -o /Quantis-PCI/src/linux/driver/Module.symvers -w  /Quantis-PCI/src/linux/driver/quantis.o
/bin/sh: scripts/mod/modpost: not found
make[3]: *** [__modpost] Error 127
make[2]: *** [modules] Error 2
make[2]: Leaving directory `/usr/src/linux-source-2.6.20'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/Quantis-PCI/src/linux/driver'
cd: 1: can't cd to lib
cd: 1: can't cd to qrng
make: *** [all] Error 2
root@sapura-desktop:/Quantis-PCI/src/linux# 



---

