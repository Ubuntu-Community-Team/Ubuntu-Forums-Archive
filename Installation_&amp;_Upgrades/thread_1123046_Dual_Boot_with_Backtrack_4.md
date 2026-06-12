---
title: "Dual Boot with Backtrack 4"
date: 2009-04-11
forum: Installation &amp; Upgrades
---

### Post by dazzler on 2009-04-11
*SOLVED* its okay managed to work it out myself, i know amazing i'm learning ;)

Could someone please give me some help editing my menu.lst to get Backtrack working.

Ive installed Backtrack on to sda4 but i'm getting an error 18 trying to boot from grub

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9038    72597703+  83  Linux
/dev/sda2   *        9039       12034    24065370    7  HPFS/NTFS
/dev/sda3           14265       14593     2642692+   5  Extended
/dev/sda4           12035       14264    17912475   83  Linux
/dev/sda5           14265       14593     2642661   82  Linux swap / Solaris

```

This is the kernel list from backtrack

```
dazzler@dazzler-laptop:/media/disk/boot$ ls
bootinst.bat  dos        liloinst.sh   pxelinux.cfg   vesamenu.c32
bootinst.sh   initrd.gz  msramdmp.c32  splash.initrd  vmlinuz
chain.c32     isolinux   mt86p         syslinux

```

And finally the relevant menu.lst entry

```
### END DEBIAN AUTOMAGIC KERNELS LIST
title Backtrack 4
root (hd0,0)
kernel (hd0,3)/boot/vmlinuz rw root=/dev/sda4
initrd (hd0,3)/boot/splash.initrd
chainloader +1


```

Many thanks

---

