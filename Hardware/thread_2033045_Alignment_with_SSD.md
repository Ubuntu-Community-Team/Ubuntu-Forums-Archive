---
title: "Alignment with SSD"
date: 2012-07-25
forum: Hardware
---

### Post by WanchoPiskado on 2012-07-25
Hi!

A few days ago i got my first SSD (OCZ Petrol 128 Gb). :D
Installed Ubuntu 12.04 on it and it works great! Trim enabled in FSTAB. I got a question tho. I did not align the partitions before installing Ubuntu. Will this be a problem? And can I align the partition after i installed Ubuntu without uninstalling everything?

---

### Post by cortman on 2012-07-25
> **WanchoPiskado said:**
> Hi!

A few days ago i got my first SSD (OCZ Petrol 128 Gb). :D
Installed Ubuntu 12.04 on it and it works great! Trim enabled in FSTAB. I got a question tho. I did not align the partitions before installing Ubuntu. Will this be a problem? And can I align the partition after i installed Ubuntu without uninstalling everything?

I went through this with my netbook SSD, and I found that Parted/GParted align cylinders correctly for SSDs by default. Nothing to worry about. :)

---

### Post by oldfred on 2012-07-25
+1 on cortman' post

New versions of gdisk, gparted and most tools have been updated in the last year or two. Unless you used an old copy of Ubuntu or gparted you should be ok.

You can check, actual alignment is 8 sectors, so just list and see if you can divide by 8.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

### Post by ahallubuntu on 2012-07-25
Yes, 12.04 LTS should align partitions automatically.

10.04 LTS for anyone else reading this does NOT align partitions correctly on "advanced format" drives. Starting(?) with 11.04, fdisk and parted align partitions correctly - I have used 11.04 to create partitions on these drives and verified the alignments were correct.

---

### Post by WanchoPiskado on 2012-07-25
Thanks guys!

---

