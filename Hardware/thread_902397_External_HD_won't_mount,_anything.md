---
title: "External HD won't mount, anything"
date: 2008-08-27
forum: Hardware
---

### Post by lesterness on 2008-08-27
My external HD (Samsung HM121HI USB) seems to be corrupted.  I have been using it with both Windows XP and with Xubuntu successfully for some months.  Now, neither will open it up.  Windows will mount it but shows no F:/ or G:/ .  Xubuntu ignores it.  When I follow suggestions in Ubuntu Forums, sudo ntfsfix /dev/sdb1 tells me:

sudo fdisk -l



Disk /dev/sda: 40.0 GB, 40007761920 bytes

255 heads, 63 sectors/track, 4864 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0xfffdb05b



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1   *           1         961     7719201    7  HPFS/NTFS

/dev/sda2             962        4864    31350847+   5  Extended

/dev/sda5             962        4748    30419046   83  Linux

/dev/sda6            4749        4864      931738+  82  Linux swap / Solaris



Disk /dev/sdb: 120.0 GB, 120034123776 bytes

255 heads, 63 sectors/track, 14593 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x74feafb1



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb3            2165        7266    40981815    5  Extended



If I try sudo apt-get install ntfsprogs , the program loads OK in Xubuntu, but when I run sudo ntfsfix /dev/sdb3 , I am told 

 sudo ntfsfix /dev/sdb3

Mounting volume... Failed to startup volume: Invalid argument.

FAILED

Attempting to correct errors... FAILED

Failed to startup volume: Invalid argument.

Volume is corrupt. You should run chkdsk.


I am pretty sure chkdsk is a DOS utility.  In Windows, I get no F:/ or G:/ , remember, so I can't run chkdsk on the HD. 

What should I try next?

lesterness

---

### Post by mocoloco on 2008-08-28
Maybe you already solved this problem, but I found a [forum with a similar issue]("http://www.dslreports.com/forum/r18915155-Volume-is-corrupt-run-chkdsk-Whats-the-command"), and the second to last post shows his solution, boot from XP CD, run recovery console and run chkdsk.
Or if you're ok with just wiping the drive you can install gparted and reformat, then it would be mountable.

---

