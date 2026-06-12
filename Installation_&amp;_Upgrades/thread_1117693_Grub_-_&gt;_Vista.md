---
title: "Grub - &gt; Vista"
date: 2009-04-06
forum: Installation &amp; Upgrades
---

### Post by aymeba on 2009-04-06
Hi All,

Ich want to reconfigure my Grub to Dualboot with Vista.

Ich have tried this Command :

first fdisk -l

[PHP]
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7a5d7a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2        3187    25591545    f  W95 Ext'd (LBA)
/dev/sda2   *        3188        6374    25597952    6  FAT16
/dev/sda3            6375       10198    30716280    7  HPFS/NTFS
/dev/sda4           14661       19457    38531902+  83  Linux
/dev/sda5               2        3187    25591513+   7  HPFS/NTFS

[/PHP]

sudo grub 

then
[PHP]
grub> root (hd0,
 Possible partitions are:
   Partition num: 1,  Filesystem type unknown, partition type 0x6
   Partition num: 2,  Filesystem type unknown, partition type 0x7
   Partition num: 3,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x7

grub> root (hd0,1)

grub> setup (hd0,
 Possible partitions are:
   Partition num: 1,  Filesystem type unknown, partition type 0x6
   Partition num: 2,  Filesystem type unknown, partition type 0x7
   Partition num: 3,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 4,  Filesystem type unknown, partition type 0x7

grub> setup (hd0) 

Error 17: Cannot mount selected partition

[/PHP]

menu.lst :

[PHP]

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		5e4bf39f-eeef-4174-ba98-5f46e8fe3805
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5e4bf39f-eeef-4174-ba98-5f46e8fe3805 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		5e4bf39f-eeef-4174-ba98-5f46e8fe3805
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=5e4bf39f-eeef-4174-ba98-5f46e8fe3805 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
uuid		5e4bf39f-eeef-4174-ba98-5f46e8fe3805
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

[/PHP]
Can you help me please?

Thanks

---

### Post by ronparent on 2009-04-06
Boot to ubuntu/ Open a terminal and type:

sudo grub
grub> find /boot/grub/stage2

This last stement will locate your ubuntu install. Use the locarion output, probably (hd0,1) or whatever as follows:

grub> root (hd0,3)
setup (hd0)

This should rewrite your menu.lst to permit you to boot to windows if a valid windows install is found.

---

