---
title: "Trying to partition SATA with XP installed"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by ppyvras on 2005-04-13
160GB SATA Maxtor hard drive on ASUS A7V600 with Via KT600 chipset

XP installed on whole drive at present using approx 60GB of the space
Want to partition drive so that the NTFS partition is reduced to 80GB and use the remainder for the Ubuntu install

I have the Release candidate version of Hoary but this has worked on a Windows 2000/IDE system

During install, at 'Partition Disks' menu
 - select: manually edit partition table
 - select: #1 primary 163.9 GB (arrow/lightning thingy) NTFS
 - displays: use as: do not use, bootable flag: on, size: 163.9 GB
 - select: size
 - displays: write changes to disk and resize partition
 - select: Yes
 - select: new partition size, 100 GB (have tried 50%, 70%, 80GB, 80 GB)
 - after a pause: returns to partition disks menu with partition table unaltered

I am new to all this but was really confident after getting it working first time on an old system.  I haven't found any posts about this either here or on google.

Would welcome any help

Cheers

Rob [-o<

---

### Post by philipacamaniac on 2005-04-13
Can the Ubuntu installer repartition/resize NTFS volumes? I'm not 100% positive, but I don't think so... Resizing an NTFS partition with data on it would almost certainly destroy the data.

Not even Windows XP itself can repartition/resize an NTFS volume if it is the primary volume, and has data on it. Your options are similar to what mine were: buy a second hard drive, or reinstall Windows, but set the Primary partition to 80GB.

I bought a 30GB for Linux, and split up my 80GB Windows drive so that half is NTFS (drive c), and half is FAT32. That way you can save data from both Windows and Linux easily. You can do that, or you can reinstall Windows (which most people have to do regularly).

---

### Post by ppyvras on 2005-04-13
i managed to resize the windows 2000 partition on another computer and I think that was NTFS.  That all works ok.  I thought installations like this ran packages such qparted or ntfsresize that were capable of doing the job.

---

### Post by ppyvras on 2005-04-15
For anyone that is interested.  Finally figured out what was going wrong.

My NTFS file system contained errors (for reasons unknown).  The ubuntu installation's response to this was just to return back to the partitioning main menu.  The only way I found out was to load the system rescue cd ([www.sysresccd.org](http://www.sysresccd.org/) /) and try and run qt_parted, the partition magic clone.

When I tried to resize the partition with that it came back with 'bad clusters'.  I tried running ntfsresize directly and that finally suggested running chkdsk utility within windows.  Going one better, I ran the full disk checking facility at administrative tools >>disk management and set it to repair any errors.

After that the ubuntu installation ran perfectly. :razz:

---

