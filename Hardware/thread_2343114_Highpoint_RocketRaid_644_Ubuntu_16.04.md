---
title: "Highpoint RocketRaid 644 Ubuntu 16.04"
date: 2016-11-13
forum: Hardware
---

### Post by jarush on 2016-11-13
I rebuilt my system that was running 16.04 and re-used my Highpoint Rocketraid 644 E-SATA card in the new system.  I installed 16.04 on the new system as well.  I'm unable to get the rr64x driver to compile.

I followed the instructions here on my original system:
[https://help.ubuntu.com/community/RocketRaid](https://help.ubuntu.com/community/RocketRaid)
And even moved the source tarball from the old system, however I'm unable to get it to compile... I'm guessing some packages have since been updated?  The old system has kernel 4.2.0-23.

Build error is:

```
root@uberchive:~/rr64x-linux-src-v1.1/product/rr64x/linux# make
make[1]: Entering directory '/usr/src/linux-headers-4.4.0-47-generic'
  CC [M]  /root/rr64x-linux-src-v1.1/product/rr64x/linux/.build/os_linux.o
  CC [M]  /root/rr64x-linux-src-v1.1/product/rr64x/linux/.build/osm_linux.o
/root/rr64x-linux-src-v1.1/product/rr64x/linux/.build/osm_linux.c:2111:2: error: unknown field âproc_infoâ specified in initializer
  proc_info:               hpt_proc_info26,
  ^
/root/rr64x-linux-src-v1.1/product/rr64x/linux/.build/osm_linux.c:2111:27: warning: initialization from incompatible pointer type [-Wincompatible-pointer-types]
  proc_info:               hpt_proc_info26,
                           ^
/root/rr64x-linux-src-v1.1/product/rr64x/linux/.build/osm_linux.c:2111:27: note: (near initialization for âdriver_template.proc_dirâ)
scripts/Makefile.build:258: recipe for target '/root/rr64x-linux-src-v1.1/product/rr64x/linux/.build/osm_linux.o' failed
make[2]: *** [/root/rr64x-linux-src-v1.1/product/rr64x/linux/.build/osm_linux.o] Error 1
Makefile:1418: recipe for target '_module_/root/rr64x-linux-src-v1.1/product/rr64x/linux/.build' failed
make[1]: *** [_module_/root/rr64x-linux-src-v1.1/product/rr64x/linux/.build] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-4.4.0-47-generic'
../../../inc/linux/Makefile.def:102: recipe for target 'rr64x.ko' failed
make: *** [rr64x.ko] Error 2



```

---

