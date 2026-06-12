---
title: "Array shows as wrong size - error loading journal"
date: 2009-01-16
forum: Installation &amp; Upgrades
---

### Post by AndyInNYC on 2009-01-16
OK, here's the basic situation:

My Ubuntu server has been running fine with a hardware RAID 5 card and 5 250 GB ATA drives.

I purchased a 3ware 9500S-8 card (SATA RAID) and installed it in a temp machine and installed Ubuntu 8.0X on a 120 GB ATA drive.

I then copied all the contents from my 1 TB RAID array onto the new (4 1 TB drives) 3 TB RAID 5 array.

No problems.

I then pulled the drive and pulled the entire array and dropped then into the machine which is actually the fileserver (took all the old boot + RAID drives + RAID card out).

When I boot, I can't access the RAID array - dmesg | tail returns the following:


[  396.647455] attempt to access beyond end of device
[  396.647465] sda1: rw=0, want=2929201176, limit=1564344319
[  396.647469] JBD: IO error reading journal superblock
[  396.647476] EXT3-fs: error loading journal.

and the partitioner shows the 'drive' as being 750 GB.

I don't want to jump through hoops and lose the data on the drive (thus forcing me to try to get the old array working in the spare machine and recopy/re-setup the entire shooting match).

Any suggestions?  I really thought I could drop the array in a new machine, although I thought I might have to reinstall Ubuntu.

Thanks in advance.

Andrew

---

### Post by AndyInNYC on 2009-01-17
Is there a solution to this, or am I SOL?

I was of the impression that one could move an array from one machine to another and still get it to work - the new machine is, literally, a new machine so it is clearly more compatible rather than less.

Help?

Andrew

---

