---
title: "Raid"
date: 2008-06-20
forum: Hardware
---

### Post by lobdellb on 2008-06-20
Until recently I had a Madrake Linux system with a RAID-1 array to keep my files save, which was comprised of 2x 250 gb hard disks.  That system had a 3rd non-raid hard disk which kept the root file system.

The root hard disk failed, so now I want to install ubuntu on another root hard disk which I have done successfully.

I have yet to successfully mount my raid array on ubuntu and I wonder if someone can tell me where I went wrong:

I did this:
 mdadm --examine --brief --scan --config=partitions 

and it confirmed that my raid disks existed and gave information consistent with my expectations.


Next I did this:
 mdadm -Ac partitions -m 0 /dev/md0 

and it created /dev/md0

Next I did this:
mount -t ext3 -r /dev/md0 /mnt/disk

and it tells me the superblock is bad, etc and that it cannot mount the filesystem.


I tried this individually on both of the two disks in my raid array (either of which should contain a copy of the filesystem), and found the same result with both.

I feel fairly confident that the filesystem on the raid drive is intact, as I tested this while the root hard drive was in its death throes.

Does anyone know where I went wrong or what the problem might be?

Thanks!

---

### Post by intel on 2008-06-20
boot into a knoppix liveCD/DVD
and fsck the Raid1 disks individually

then try mounting the raid1s under ubuntu

intel

---

### Post by lobdellb on 2008-07-03
knoppix automatically mounted the drive.

I'm not sure why ubuntu didn't, and wouldn't no matter how I asked.

---

