---
title: "Adaptec 3405 array doesn't show up in new 10.04 LTS install"
date: 2010-08-29
forum: Hardware
---

### Post by billmilosz on 2010-08-29
I have a Windows XP32 machine, boots off an IDE drive. I have an Adaptec 3405 raid card in this machine with a RAID5 array.  Works fine in Windows. Shows up as F:, it is NTFS.

Installed Lucid on another partition on the IDE drive, that all went fine. Except, the Adaptec RAID5 array does not show up in Lucid.

I installed gparted (I am more familiar with gparted than the new disk manager) and looked around, I could see the Adaptec device but it said the partition was "not recognized" -

Rebooted into XP and all is well, the RAID5 array is OK, etc etc.  Back into Lucid, no partition in the RAID5 array is showing up.

What's going on?  Why isn't the NTFS partition in my RAID5 array showing up? This is HARDWARE RAID, supposed to work great in Linux.

I can see the NTFS partition on the IDE drive in Lucid, I can read it, write to it, it's all fine. So it's not a problem with NTFS filesystems in Lucid.

In Lucid, in gparted I have the option to format the unrecognized partition, but I am not particularly keen to lose 1.6 TB of data, or go through the tremendous hassle of copying my 1.6 TB of data to a USB drive, formatting the RAID5 array, and then copying the data back.  That much data, this would take DAYS.

Any suggestions?

---

