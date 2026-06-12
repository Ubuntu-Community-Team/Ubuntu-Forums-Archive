---
title: "Another &quot;Error 21: Cannot find Hard Disk&quot; error"
date: 2008-12-15
forum: Installation &amp; Upgrades
---

### Post by Ubuntiac on 2008-12-15
Hi everyone,

I've got Grub booting just fine, which also boots Kubuntu 8.10 fine as well (on HD1,0). Trouble is that my (*shudder*) XP install (which was installed before Kubuntu) is just coming up with an error 21.

I suspect this has to do with the fact that it's on hd2,1 not hd0,0, but wierdly enough, when I installed XP, it only seemed to be able to see hd2. Mapping is set to swap hd 0 and 2 though.

[LIST]
[*]Grub and then root (hd0,0) it also returns error 21 "Selected Disk does not Exist."
[*]find /boot/grub/stage 1 returns "Error 15: File not found"
[*]QTparted sees all drives and partitions perfectly.
[/LIST]

The possible only thing I can see is that Ubuntu is identifying drives by UUID whereas XP is identifying by (HDx,y).

Full Menu.lst is attached. Abbreviated version without old kernels is below.

Thanks for helping to make such a supportive and helpful community! :)

> title Ubuntu 8.10, kernel 2.6.27-10-generic
kernel /boot/vmlinuz-2.6.27-10-generic root=UUID=ec5b2f27-9e76-47e4-81f1-7a2eae4d964d ro quiet splash
initrd /boot/initrd.img-2.6.27-10-generic

title Ubuntu 8.10, kernel 2.6.27-10-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-10-generic root=UUID=ec5b2f27-9e76-47e4-81f1-7a2eae4d964d ro  single
initrd /boot/initrd.img-2.6.27-10-generic

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Microsoft Windows XP Home Edition
root (hd2,1)
map (hd2) (hd0)
map (hd0) (hd2)
chainloader +1
savedefault
makeactive

---

### Post by logos34 on 2008-12-15
post your

sudo fdisk -l

> find /boot/grub/stage 1 returns "Error 15: File not found"

actually should be find /boot/grub/stag**e1** (no space) -- but maybe that's just a typo in your post

you might try:

> title Microsoft Windows XP Home Edition
root (hd**1**,1)
map (hd**1**) (hd0)
map (hd0) (hd**1**)
chainloader +1
savedefault
makeactive

---

### Post by Ubuntiac on 2008-12-15
Thanks Logos34,

I'll give that a try now.

Output of fdisk -l is:


> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdebf17c9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11473    92156841   83  Linux
/dev/sda2           12745       24321    92992252+   7  HPFS/NTFS
/dev/sda3           11474       12744    10209307+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xce3eaaa7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3517    28250271   83  Linux
/dev/sdb3            3518       24321   167108130   83  Linux

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d782d78

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       21597   173477871   83  Linux
/dev/sdc2   *       21598       24321    21880530    7  HPFS/NTFS

---

### Post by Ubuntiac on 2008-12-15
Beautiful.

Going with hd1,1 did the trick. Many thanks!

---

### Post by logos34 on 2008-12-15
glad to hear it's fixed! enjoy

---

