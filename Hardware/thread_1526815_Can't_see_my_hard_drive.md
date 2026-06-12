---
title: "Can't see my hard drive"
date: 2010-07-08
forum: Hardware
---

### Post by fun2jog on 2010-07-08
Due to Windows "error loading operating system" I decided to try Ubuntu.  Boot from DVD when great, but can't see my hard drive. Checked under computer, file system, but not there. Where could it be?  Thanks

---

### Post by Joe of loath on 2010-07-08
It should be in 'Computer'. Due to the error you had, it might be dead. Open the terminal (In applications>accessories) and type ```
sudo fdisk -l
``` and post the output.

---

### Post by fun2jog on 2010-07-08
Here's what I got.  What now?  Thanks

[FONT=arial][SIZE=2][COLOR=black][SIZE=2][FONT=Arial, Helvetica, sans-serif]ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        9728    78075900    7  HPFS/NTFS[/FONT][/SIZE][/COLOR][/SIZE][/FONT]

---

