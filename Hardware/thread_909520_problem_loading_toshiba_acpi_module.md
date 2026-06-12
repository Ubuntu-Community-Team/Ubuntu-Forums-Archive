---
title: "problem loading toshiba_acpi module"
date: 2008-09-03
forum: Hardware
---

### Post by esytm007@yahoo.com on 2008-09-03
WHAT SHOULD I DO WITH THIS ERROR?
the modules do not loaded in my laptop i need them please help me.

toshiba A100-632 (PSAARE)
ubuntu 8.04 LTS 
kernel 2.6.24-16-generic

root@e-laptop:~# modprobe toshiba_acpi
FATAL: Error inserting toshiba_acpi (/lib/modules/2.6.24-16-generic/kernel/drivers/acpi/toshiba_acpi.ko): No such device

root@e-laptop:~# modprobe toshiba
FATAL: Error inserting toshiba (/lib/modules/2.6.24-16-generic/kernel/drivers/char/toshiba.ko): No such device



I test omnibook source but it does not work either
root@e-laptop:/media/disk/a/bb/omnibook-2.20070211+svn20071217# make 
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/media/disk/a/bb/omnibook-2.20070211+svn20071217 modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic' 
 
  ERROR: Kernel configuration is invalid. 
         include/linux/autoconf.h or include/config/auto.conf are missing. 
         Run 'make oldconfig && make prepare' on kernel src to fix it. 
 
 
  WARNING: Symbol version dump /usr/src/linux-headers-2.6.24-16-generic/Module.symvers 
           is missing; modules will have no dependencies and modversions. 
 
  Building modules, stage 2. 
/usr/src/linux-headers-2.6.24-16-generic/scripts/Makefile.modpost:42: include/config/auto.conf: No such file or directory 
make[2]: *** No rule to make target `include/config/auto.conf'. Stop. 
make[1]: *** [modules] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic' 
make: *** [omnibook.ko] Error 2 
root@e-laptop:/media/disk/a/bb/omnibook-2.20070211+svn20071217# depmod -a 
root@e-laptop:/media/disk/a/bb/omnibook-2.20070211+svn20071217# make 
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/media/disk/a/bb/omnibook-2.20070211+svn20071217 modules 
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic' 
 
  ERROR: Kernel configuration is invalid. 
         include/linux/autoconf.h or include/config/auto.conf are missing. 
         Run 'make oldconfig && make prepare' on kernel src to fix it. 
 
 
  WARNING: Symbol version dump /usr/src/linux-headers-2.6.24-16-generic/Module.symvers 
           is missing; modules will have no dependencies and modversions. 
 
  Building modules, stage 2. 
/usr/src/linux-headers-2.6.24-16-generic/scripts/Makefile.modpost:42: include/config/auto.conf: No such file or directory 
make[2]: *** No rule to make target `include/config/auto.conf'. Stop. 
make[1]: *** [modules] Error 2 
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic' 
make: *** [omnibook.ko] Error 2

---

