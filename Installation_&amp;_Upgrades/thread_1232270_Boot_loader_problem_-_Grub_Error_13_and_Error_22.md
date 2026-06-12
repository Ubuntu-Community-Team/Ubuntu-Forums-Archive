---
title: "Boot loader problem - Grub Error 13 and Error 22"
date: 2009-08-05
forum: Installation &amp; Upgrades
---

### Post by symmys on 2009-08-05
I'm starting a new thread here because in the Absolute beginners I've got no reply yet. If I am wrong please delete this or the other thread.
 
I had WinXp installed on my primary Hdisk and Ubuntu 8.04 installed on a second disk. Boot loader was on the first disk. 

I have installed Ubuntu 9.04 on the second disk and the (new) boot loader on the second disk. Now I can boot in Ubuntu from the second disk but not in WinXP. When I try to boot in WinXP from the second disk I get the message "Grub Error 13: "Invalid or unsupported executable format". 
 
When I try to boot from the first disk I get Error 22.

Any help? 

My menu.lst:

```
title Ubuntu 9.04, kernel 2.6.28-14-generic
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=f6d37e71-1227-485f-9001-c01cb8333bc6 ro quiet splash
initrd /boot/initrd.img-2.6.28-14-generic

title Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-14-generic root=UUID=f6d37e71-1227-485f-9001-c01cb8333bc6 ro  single
initrd /boot/initrd.img-2.6.28-14-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=f6d37e71-1227-485f-9001-c01cb8333bc6 ro quiet splash
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
kernel /boot/vmlinuz-2.6.28-11-generic root=UUID=f6d37e71-1227-485f-9001-c01cb8333bc6 ro  single
initrd /boot/initrd.img-2.6.28-11-generic

title Ubuntu 9.04, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Microsoft Windows XP Professional
root (hd0,0)
chainloader +1
savedefault
makeactive
```

My fdisk -l

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbad6bad6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb4dcb4dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9331    74951226   83  Linux
/dev/sdb2            9332        9729     3196935    5  Extended
/dev/sdb5            9332        9729     3196903+  82  Linux swap / Solaris

```

---

