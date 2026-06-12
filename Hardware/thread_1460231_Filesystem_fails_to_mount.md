---
title: "Filesystem fails to mount"
date: 2010-04-22
forum: Hardware
---

### Post by rannuG on 2010-04-22
Over the last weeks, the chances of the system booting up have been about 50/50. I often get error messages like these:

```
Gave up waiting for root device. Common problems:
- Boot args (cat proc/cmdline)
   - Check rootdelay = (did the system wait long enough?)
   - Check root = (Did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
Alert! /dev/disk/by-uuid/936d0df3-fc17-4ae8-9480-15ef3657f49c does not exist. Dropping to a shell!
   BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu7) built-in shell (ash)
   Enter 'help' for a list of built-in commands.
```And less frequently:

```
swapon failed: device or resource busy
mountall: terminated with status 255
problem activating swap: dev/disk/by-uuid/936d0df3-fc17-4ae8-9480-15ef3657f49c
/dev/sda1 contains a file system with errors, check forced.
    /dev/sda1: UNEXPECTED INCONSISTENCY. RUN fsck MANUALLY.
    mountall: fsck / [750] terminated with status 4
    mountall: filesystem has errors: /
    init: mountall main process (746) terminated with status 3
    Mount of filesystem failed.
    A maintenance shell will now be started.
```I think there's definitely something wrong with some of my hardware as I had these same problems on my Jaunty before I made a fresh Karmic installation.

My computer is approximately 3 years old. It has the following:

Processors: 4x Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz
Memory: 2GB
Motherboard: Gigabyte P35-DS3
450 GB filesystem
The operating system is Ubuntu 9.10 with the Linux 2.6.31-20-generic (i686) kernel.

I've tried running [COLOR=red]fsck /dev/sda1[/COLOR] numerous times: on a live cd, running recovery mode and when dropping to a shell. The problem just seems to come back next time I boot up the computer.




Any ideas of what's going on?

---

### Post by elliotn on 2010-04-22
fsck 

in cli
i think

---

### Post by elliotn on 2010-04-22
i meant type fsck when it give u a command line.

---

