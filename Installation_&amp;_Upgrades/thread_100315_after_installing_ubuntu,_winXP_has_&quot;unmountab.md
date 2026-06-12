---
title: "after installing ubuntu, winXP has &quot;unmountable boot volume&quot; error"
date: 2005-12-07
forum: Installation &amp; Upgrades
---

### Post by djalias on 2005-12-07
please help with this, it would be greatly appreciated. i will explain what happened as well as i can:

Basically, i wiped my drive, and then made an primary NTFS partition and installed XP on it. Then partitioned the  remaining space into a primary linux partition, and an extended linux swap partition. I then installed ubuntu on those partitions and then installed GRUB to the linux partition and set the MBR to boot the linux partition. Ubuntu boots fine, but when i try to boot xp, it gives me a BSOD with "unmountable boot volume" as the error. I have tried setting the MBR to boot the windows partition directly, bypassing grub, but the same problem occurs. I have a thinkpad T41 with the latest bios update and a 30gb drive. I have tried using the windows recovery console but it cant find the drive. Here is the output of fdisk in ubuntu and my grub conf.

FDISK:
Disk /dev/hda: 30.0 GB, 30005821440 bytes
15 heads, 63 sectors/track, 62016 cylinders
Units = cylinders of 945 * 512 = 483840 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       32512    15361888+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/hda2   *       32522       60741    13333950   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/hda3           60742       62016      602437+   5  Extended
Partition 3 does not end on cylinder boundary.
/dev/hda5           60742       62016      602406   82  Linux swap / Solaris

GRUB (without default options):
## ## End Default Options ##

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
chainloader     +1


if there is anything you could suggest, that would be great!

---

