---
title: "2 GRUB questions"
date: 2009-06-08
forum: Installation &amp; Upgrades
---

### Post by superhaus on 2009-06-08
I have a small partition on my hard drive that I decided to use to dual-boot Windows. Unfortunately, I already had Ubuntu set up the way I like so installing Windows first, then Ubuntu wasn't really an option. I got Windows installed, then used a live CD to allow me to boot back into Ubuntu, but now I am not really sure how to fix GRUB so that I can boot either OS.

Here is an output of fdisk -l:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x53cd23c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       23636   189856138+  83  Linux
/dev/sda2   *       23637       29267    45230080    7  HPFS/NTFS
/dev/sda3           29268       30401     9108855    5  Extended
/dev/sda5           29268       30401     9108823+  82  Linux swap / Solaris

Disk /dev/sdb: 7916 MB, 7916748800 bytes
244 heads, 62 sectors/track, 1022 cylinders
Units = cylinders of 15128 * 512 = 7745536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

So, 2 questions:
1. Why is /dev/sda1 not marked as bootable, when I just booted into it?
2. What do I need to add to GRUB to get the Windows partition to show up?

Thanks

---

### Post by coffeecat on 2009-06-08
> **superhaus said:**
> 1. Why is /dev/sda1 not marked as bootable, when I just booted into it?

The active or boot flag is only needed for Windows. Linux does not need the boot flag.

> **superhaus said:**
>  2. What do I need to add to GRUB to get the Windows partition to show up?

Open menu.lst in a text editor with root privileges with:

```
gksudo gedit /boot/grub/menu.lst
```and add this stanza:

```
title     Windows
rootnoverify     (hd0,1)
makeactive
chainloader     +1
boot
```

---

