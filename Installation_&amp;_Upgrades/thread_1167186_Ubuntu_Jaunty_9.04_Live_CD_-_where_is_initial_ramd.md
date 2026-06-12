---
title: "Ubuntu Jaunty 9.04 Live CD - where is initial ramdisk?"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by hal8000 on 2009-05-22
After a failed desktop install of Ubuntu 9.04  (install failed at 94% and grub and kernel never installed), I though I'd boot the live CD and copy the systems working kernel and initial ramdisk.

Im posting from live CD right now, but there appears no sign of the initial ramdisk??

The / directory links initrd to /boot  :-

ubuntu@ubuntu:~$ ls -l /in*
lrwxrwxrwx 1 root root 33 2009-04-20 14:05 /initrd.img -> boot/initrd.img-2.6.28

However listing the contents of /boot prove otherwise :-

ubuntu@ubuntu:~$ ls -lh /boot
total 2.2M
-rw-r--r-- 1 root root 517K 2009-04-17 03:41 abi-2.6.28-11-generic
-rw-r--r-- 1 root root  95K 2009-04-17 03:41 config-2.6.28-11-generic
-rw-r--r-- 1 root root 126K 2009-03-27 17:15 memtest86+.bin
-rw-r--r-- 1 root root 1.4M 2009-04-17 03:41 System.map-2.6.28-11-generic
-rw-r--r-- 1 root root 1.1K 2009-04-17 03:43 vmcoreinfo-2.6.28-11-generic


So where is initrd.img  for the live CD?
Thanks in advance.

---

