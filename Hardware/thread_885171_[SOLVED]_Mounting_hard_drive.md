---
title: "[SOLVED] Mounting hard drive"
date: 2008-08-09
forum: Hardware
---

### Post by Ghoztrider on 2008-08-09
Good Evening,

I have an internal back up hard drive that I took out of another pc and i'm trying to get it to work on my Hardy machine. I have a "cables to go" adapter that lets me connect it to another machine externally. It shows up in "My Computer" as a USB drive. When I go to double click it it comes up with -- Unable to mount location, can't mount file. What if any, other options do I have, or what do I need to do to get this to mount? Thanks.


Shawn

---

### Post by cdtech on 2008-08-09
can you post the output of "sudo fdisk -l" and lets see what gives.

thanks.......

---

### Post by Ghoztrider on 2008-08-09
Here it is:

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9726    57641220    5  Extended
/dev/sda5            2551        9427    55239471   83  Linux
/dev/sda6            9428        9726     2401686   82  Linux swap / Solaris

Thanks

---

### Post by cdtech on 2008-08-09
That shows only one drive (primary drive). No other drives are connected.

---

