---
title: "Grub error 17 - Tried everything!!"
date: 2009-08-18
forum: Installation &amp; Upgrades
---

### Post by mgt81 on 2009-08-18
hi guys, i'm not super new to linux but i wouldn't say i'm seasoned yet. I'm having the below problems with my installation of 9.04.

my grub 1.5 gives me the error 17 at boot up. i'd say this is due to resizing the partitions and deleting a few to get the extra size in the first place. the ones i deleted were, i thought, unnecessary, having only the lost and found folder inside, and not having / or boot listed next to them in partitiion editor.
when i resized them using a live cd (after about 15 hours) the operation crashed. i retried and this time it worked, so i rebooted, removed the lived CD and got an error 22 from grub. since then i've  reinstalled grub to the partition (sda8 at the time, since renumbered to sda 5 using fdisk). i have tried various different solutions from various forums, and have had no success, apart from the error changing from 22 to 17 and back, depending on what i tried. my partition table is completely screwed, i think. i've edited /boot/grub/menu.lst and fstab to mirror the location of the linux boot partition, but to no avail. the output of fdisk -l can be seen below:

**************************************************************************
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?      967718     1242132   272218546+  20  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(356, 97, 46) logical=(967717, 6, 59)
Partition 1 has different physical/logical endings:
     phys=(357, 116, 40) logical=(1242131, 2, 23)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?      670456      942118   269488144   6b  Unknown
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 110, 57) logical=(670455, 23, 57)
Partition 2 has different physical/logical endings:
     phys=(269, 101, 57) logical=(942117, 5, 52)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?      271669      976489   699181456   53  OnTrack DM6 Aux3
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(345, 32, 19) logical=(271668, 1, 18)
Partition 3 has different physical/logical endings:
     phys=(324, 77, 19) logical=(976488, 1, 49)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   *      702938      702949       10668+  49  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(87, 1, 0) logical=(702937, 10, 36)
Partition 4 has different physical/logical endings:
     phys=(335, 78, 2) logical=(702948, 2, 44)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
**************************************************************************
This is what it looks like in partition editor:

[IMG]http://img196.imageshack.us/img196/9665/gpartedj.png[/IMG]

Have i totally ruined my installation and lost all the files i've added since my last backup? my menu.lst and fstab can be seen below:

[SIZE="5"]Menu.lst:
[/SIZE]
title		Ubuntu 9.04, kernel 2.6.28-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-14-generic root=dev/sda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-14-generic root=dev/sda5 ro  single
initrd		/boot/initrd.img-2.6.28-14-generic

title		Ubuntu 9.04, kernel 2.6.28-13-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-13-generic root=dev/sda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-13-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-13-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.28-13-generic root=dev/sda5 ro  single
initrd		/boot/initrd.img-2.6.28-13-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-14-generic root=dev/sda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.27-14-generic root=dev/sda5 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.24-24-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-24-generic root=dev/sda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.24-24-generic
quiet

title		Ubuntu 9.04, kernel 2.6.24-24-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.24-24-generic root=/dev/sda5 ro  single
initrd		/boot/initrd.img-2.6.24-24-generic

title		Ubuntu 9.04, kernel 2.6.22-14-generic
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=dev/sda5 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 9.04, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.22-14-generic root=dev/sda5 ro  single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

*************************************************************************
[COLOR="black"][SIZE="5"]Fstab[/SIZE][/COLOR]:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=5e81bc88-27b5-4335-8948-63a80ad70c05 /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda11
UUID=31adffc2-b4b7-491a-867e-daf88ef45881 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
**************************************************************************

If anyone out there can offer me any advice or assistance I would really appreciate it :)
:guitar:

---

