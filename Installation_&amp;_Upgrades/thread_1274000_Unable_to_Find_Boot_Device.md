---
title: "Unable to Find Boot Device"
date: 2009-09-24
forum: Installation &amp; Upgrades
---

### Post by kramer2718 on 2009-09-24
Hi guys,

I am trying to install Kubuntu 9.04 onto an amd64 system.  I downloaded and burned the iso to a dvd.  I booted in to the install dvd and went through the menu.  My disk was already partitioned in to 4 partitions: 


```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bac1c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           9       72261   83  Linux
/dev/sda2              10        3994    32009512+  83  Linux
/dev/sda3            3995        6084    16787925   82  Linux swap / Solaris
/dev/sda4            6085      121601   927890302+  83  Linux

```

I went through the boot menu and selcted sda1 as boot (it's ext2), sda2 as / (it's ext3), sda3 as swap, and sda4 as /home.  I then selected my user name, etc.  The install disk did it's work and then asked me to reboot.  I then got this message:

```
Reboot and Select proper Boot device
or Insert Boot Media in selected Boot device and press a key

```

I booted back in to the kubuntu live cd and to see that the boot disk had been installed to properly.  So I mounted and listed sda1:

```

total 13815
drwxr-xr-x 4 root root    1024 2009-09-23 08:57 .
drwxr-xr-x 4 root root      80 2009-09-24 04:45 ..
-rw-r--r-- 1 root root  525592 2009-04-17 03:34 abi-2.6.28-11-generic
-rw-r--r-- 1 root root   90584 2009-04-17 03:34 config-2.6.28-11-generic
drwxr-xr-x 2 root root    1024 2009-09-23 08:57 grub
-rw-r--r-- 1 root root 7925880 2009-09-23 08:57 initrd.img-2.6.28-11-generic
drwxr-xr-x 2 root root   12288 2009-09-23 08:47 lost+found
-rw-r--r-- 1 root root  128796 2009-03-27 20:12 memtest86+.bin
-rw-r--r-- 1 root root 1871601 2009-04-17 03:34 System.map-2.6.28-11-generic
-rw-r--r-- 1 root root    1170 2009-04-17 03:39 vmcoreinfo-2.6.28-11-generic
-rw-r--r-- 1 root root 3522336 2009-04-17 03:34 vmlinuz-2.6.28-11-generic

```

Any ideas?

---

### Post by rreese6 on 2009-09-24
how about a wild guess?

go to grub folder
open menu.lst
look and see if you see "/boot/grub" anywhere, change that to "/grub"
save and reboot.

I am very tired so I am doing only a wild guess here.

---

