---
title: "External Hard Drive &amp; Pen Drive problems"
date: 2008-04-13
forum: Hardware &amp; Laptops
---

### Post by GPizza on 2008-04-13
Hi,
I've tried to find threads with similar issues that I am having now but nothing helped me so far...

Just to start: I am completely new to Ubuntu and Linux so I appreciate if you could post some replies considering that :-)

Well, I am running Ubuntu rel 7.10 (gutsy) and when I connect my LaCie external hard drive (it has its own external power source)  to the USB port of my IBM Thinkpad T40 it just don't recognize it. The same happens with my Sandisk 4GB USB pen drive.

What happens sometime is that after a while, suddenly  the hard drive is recognized and I can browse trough the files but after a few seconds it just disconnects automatically and a message that I should unmount it before disconnecting appears on the bottom right of my screen.

Here is the output of sudo fdisk -l command with my external hard drive connected to USB (HD was connected after system start up):

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbd77bd77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4676    37559938+  83  Linux
/dev/sda2            4677        4864     1510110    5  Extended
/dev/sda5            4677        4864     1510078+  82  Linux swap / Solaris

Here goes  my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=a2664037-3e1c-4565-9a2b-7686eaa084f6 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=5fa7ce33-9ba3-4c4d-a334-2f7bee43aad3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Anyone has any idea of why  this is happening and what should I do to solve this problem?

Thanks a lot!!!

---

