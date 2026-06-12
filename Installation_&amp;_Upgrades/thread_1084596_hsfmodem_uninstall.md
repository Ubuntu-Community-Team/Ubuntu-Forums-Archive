---
title: "hsfmodem uninstall"
date: 2009-03-02
forum: Installation &amp; Upgrades
---

### Post by qbox on 2009-03-02
Hi
I have Dell inspiron 1520 and some modem driver who not work at all. When system boot I loose 20-30 seconds while kernel try to compile and install this drivers and to the end he fail. In the file /tmp/hfsconfig-buildlog I have this

```
Makefile:20: *** WARNING: Trying to compile kernel modules on a x86_64 system while the installed hsf driver package is for i386, this is likely to fail... ***
(cd /lib/modules/2.6.24-23-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.24-23-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
/usr/lib/hsfmodem/modules/Makefile:20: *** WARNING: Trying to compile kernel modules on a x86_64 system while the installed hsf driver package is for i386, this is likely to fail... ***
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
(cd /lib/modules/2.6.24-23-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.24-23-generic/build" "M=/usr/lib/hsfmodem/modules/GPL/hda" "CC=gcc" "HDA_CFLAGS=-DFOUND_KZALLOC  -DFOUND_TLV   -DFOUND_IRQ_HANDLER_T -DFOUND_DELAYED_WORK  " clean)
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
rm -rf *.o GPL/*.o *.ko GPL/*.ko *.mod.c GPL/*.mod.c .*.cmd GPL/.*.cmd .tmp_versions .tmp_versions  /lib/modules/2.6.24-23-generic/build/.tmp_versions/hsfosspec.mod  /lib/modules/2.6.24-23-generic/build/.tmp_versions/hsfserial.mod  /lib/modules/2.6.24-23-generic/build/.tmp_versions/hsfengine.mod  /lib/modules/2.6.24-23-generic/build/.tmp_versions/hsfpcibasic2.mod  /lib/modules/2.6.24-23-generic/build/.tmp_versions/hsfpcibasic3.mod  /lib/modules/2.6.24-23-generic/build/.tmp_versions/hsfhda.mod  /lib/modules/2.6.24-23-generic/build/.tmp_versions/hsfmc97ich.mod  /lib/modules/2.6.24-23-generic/build/.tmp_versions/hsfmc97via.mod  /lib/modules/2.6.24-23-generic/build/.tmp_versions/hsfmc97ali.mod  /lib/modules/2.6.24-23-generic/build/.tmp_versions/hsfmc97ati.mod  /lib/modules/2.6.24-23-generic/build/.tmp_versions/hsfmc97sis.mod  /lib/modules/2.6.24-23-generic/build/.tmp_versions/hsfsoar.mod Modules.symvers GPL/hda/Modules.symvers
(cd /lib/modules/2.6.24-23-generic/build && make "CNXT_KERNELSRC=/lib/modules/2.6.24-23-generic/build" "M=/usr/lib/hsfmodem/modules" "CC=gcc" modules)
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-23-generic'
/usr/lib/hsfmodem/modules/Makefile:20: *** WARNING: Trying to compile kernel modules on a x86_64 system while the installed hsf driver package is for i386, this is likely to fail... ***
  CC [M]  /usr/lib/hsfmodem/modules/mod_engine.o
/usr/lib/hsfmodem/modules/mod_engine.c:1: error: CPU you selected does not support x86-64 instruction set
make[2]: *** [/usr/lib/hsfmodem/modules/mod_engine.o] Error 1
make[1]: *** [_module_/usr/lib/hsfmodem/modules] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-23-generic'
make: *** [all] Error 2
```

How to uninstall this driver so not be bothered any more.

Thx:confused:

---

### Post by snakdoc on 2009-04-11
make uninstall

---

