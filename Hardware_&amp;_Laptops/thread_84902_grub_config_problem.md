---
title: "grub config problem"
date: 2005-11-01
forum: Hardware &amp; Laptops
---

### Post by makisupa123 on 2005-11-01
I've been running ubuntu fo awhile.  I realize this is in no way a ubuntu problem...

I had 2 HD -- one with ubuntu and a small one for XP (gaming).  A couple fo months ago I bought a large SATA drive and moved all of my partitions onto it.  Ubuntu boots fine.  I cannot boot my XP partition.  I've tried several different menu.lst configs to no avail.  The XP partition is /dev/sda5 or in grub terms 0,4.  Here's what i've tried:

#title		Windows NT/2000/XP
#root		(hd0,4)
#savedefault
#makeactive
#chainloader	+1

#title Windows
#map (hd0) (hd4)
#map (hd4) (hd0)
#rootnoverify (hd0,4)
#savedefault
#chainloader +1 

title Windows XP
map	(hd0)	(hd4)
map	(hd4)	(hd0)
rootnoverify (hd0,4)
savedefault
makeactive
chainloader +1
boot

ignore the "#"'s -- i'm just keeping track of what i've tried.  It was necessary to use the map command to boot my XP partition when it was on another drive.  Now i get one of the following error:

Filesystem type unknown, Partition type 0x17

Error 12:  Invalid device requested

or

A disk read error occurred

i've googled left and right and would appreciate some help.
Thanks!

/mak

---

### Post by makisupa123 on 2005-11-01
something strange i just noticed...the output of fdisk -l.  Look at this:

Disk /dev/sda: 160.0 GB, 160040803840 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16650   133741093+  83  Linux
/dev/sda2           16651       19457    22547227+   f  W95 Ext'd (LBA)
/dev/sda5           16651       19261    20972826    7  HPFS/NTFS
/dev/sda6           19262       19457     1574338+  82  Linux swap / Solaris

how is it possible that sda2 and 5 begin on the same block?

---

### Post by kalin on 2005-11-01
That's fine, /dev/sda2 is simply an extended partition, i.e. /dev/sda2 is like a logical partition containing /dev/sda5 and /dev/sda6 (notice how it not only starts with sda5, but also *ends* with sda6)

---

### Post by kalin on 2005-11-01
Looks like partition type 0x17 means 'Hidden NTFS', could this be the problem? Could you check the partition type in Ubuntu?

edit: ops you did just that by using fdisk -l.

You could check the following:

1 .What does gparted say about the NTFS partition? Maybe fdisk does not care if it's a 'hidden' type.

2. Another problem might be if you moved it around (if it was previously not the 5th partition): IIRC windows has problems booting from a partition that's beyond the 1024th cylinder.

---

