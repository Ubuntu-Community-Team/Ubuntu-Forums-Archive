---
title: "grew my raid 5 with hdd instead of hdd1"
date: 2009-05-26
forum: Installation &amp; Upgrades
---

### Post by jscales on 2009-05-26
Forgive me i'm new!

I managed to grow my raid 5 array with mdadm in Server 9.04 but when I added the new drive, i added the drive but not my partition. hdd instead of hdd1.

my array is now made up of hda1 / hdb1 / hdc1 / hdd

the array is currently rebuilding.

Is this going to be ok?

What should I do?

Thank you in advance for any help!

---

### Post by lemming465 on 2009-05-30
At a guess, you are probably going to be OK.  The difference between hdd and hdd1 is whether you use all the blocks on the drive for RAID data, or just the ones specified by the partition table for hdd1.  At the OS level it's just reading and writing disk sectors, and isn't too fussy.

In case of doubt, wait for the first rebuild to finish, fail the offending hdd drive out of the RAID, repartition it, add it back, and let it rebuild again.

---

### Post by sub.mesa on 2009-05-30
You should create a partition on the disk, to prevent Windows from 'initializing' the disk thinking its empty. Also, if you switch the controller to RAID-mode (if supported) it could overwrite data causing mdraid to loose its configuration for that disk (or all disks).

---

