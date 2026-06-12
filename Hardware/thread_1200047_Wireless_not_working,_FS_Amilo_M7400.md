---
title: "Wireless not working, FS Amilo M7400"
date: 2009-06-29
forum: Hardware
---

### Post by ben22 on 2009-06-29
Hello,

on Amilo M7400, Ubuntu 9.04 I try to get wireless working, so far now success. Here is what I did so far: 

lshw -C network (wireless=radio off)

```
lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 01
       serial: 00:0a:e4:28:6a:33
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.2.108 latency=64 module=ssb multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:4d:de:22
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f2:23:8d:ab:f5:c3
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

```

Thus I tried to follow the tutorial at: 

[http://ubuntuforums.org/showthread.php?t=189540]("http://ubuntuforums.org/showthread.php?t=189540")

```
lidia@lidia-laptop:~/Desktop/fsam7400-0.5.1$ make
make -C /lib/modules/`uname -r`/build SUBDIRS=/home/lidia/Desktop/fsam7400-0.5.1 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/lidia/Desktop/fsam7400-0.5.1/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/lidia/Desktop/fsam7400-0.5.1] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [fsam7400.ko] Error 2
lidia@lidia-laptop:~/Desktop/fsam7400-0.5.1$ sudo make install
[sudo] password for lidia: 
make -C /lib/modules/`uname -r`/build SUBDIRS= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function &#8216;conf_askvalue&#8217;:
scripts/kconfig/conf.c:104: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function &#8216;conf_choice&#8217;:
scripts/kconfig/conf.c:306: warning: ignoring return value of &#8216;fgets&#8217;, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-11-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  SYMLINK include/asm -> include/asm-x86
make[2]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-11-generic'
make: *** [fsam7400.ko] Error 2
lidia@lidia-laptop:~/Desktop/fsam7400-0.5.1$ sudo modprobe fsam7400 uid=1000 autoload=0
FATAL: Error inserting fsam7400 (/lib/modules/2.6.28-11-generic/kernel/ubuntu/misc/fsam7400.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
Would be great if someone could help further!
ben

---

