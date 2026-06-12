---
title: "Problem Installing.  Seems easy to fix, just don't know how."
date: 2009-03-22
forum: Installation &amp; Upgrades
---

### Post by Vic the Trader on 2009-03-22
I already have an NTFS 200 GB partition on part of the drive.  The other 440126 Megabytes I'm trying to put Ubuntu 8.10 on.

Before creating, it displayed...
- Logical
- 440126 Megabytes
- Beginning
- Use as:  Ext 3 Journaling File System
- Mount Point: (blank)

After creating it over the free space, when I go to hit forward with a check in the format box, instead of installing Ubuntu, it says.....

"_No root file system_
No root file system is defined

Please correct this from the partitioning menu"

---

### Post by tommcd on 2009-03-22
If the 440 GB is free space you could just select the partition option to "use the largest free space", or whatever it says. This will make most of the space a root partition, and it will also create a swap partition that is about 2X the amount of memory you have.

 If you would like to use manual partitioning, which will let you set up a separate home partition for your data, then create:
 a 12-15 GB (since you have a lot of space) root partition; file type ext3; mount point / (for root).
a 1GB swap partition; this will be setup as swap.
the rest as ext3 partition; mount point /home.
Set the Windows NTFS partition as bootable; mount point /media/windows (or /media/whatever_you_want_to_call_it). Make sure "do not format" is selected for Windows. Or you could just not set a mount point for it if (as I do) you don't care about mounting you Windows partition on Ubuntu.
You should be good from there to finish the install. Write back if you need more help.

---

