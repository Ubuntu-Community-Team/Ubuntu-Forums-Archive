---
title: "Does Ubuntu recognize 6TB hard drives?"
date: 2013-03-02
forum: Hardware
---

### Post by Heeter on 2013-03-02
Hi all,

Will Ubuntu recognize a 6TB (2x3TB RAID0) Hard rive setup?

This is for my 12.10 64bit setup.

Thanks

Heeter

---

### Post by oldfred on 2013-03-02
Yes, but you have to use gpt partitioning.

But I am not a fan of RAID (except for servers) and definitely think you need to reconsider that much data in RAID 0. How are you backing up?
       Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.

---

### Post by dabl on 2013-03-02
Or, you could make a single BTRFS filesystem across both (unformatted) drives.  Using the defaults for a multi-device filesystem, you will have mirroring of metadata, and striping of your data.

[https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices](https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices)

---

### Post by oldfred on 2013-03-02
Not everyone finds btrfs works.

 BTRFS, not ready for prime time
[http://ubuntuforums.org/showthread.php?t=2111487](http://ubuntuforums.org/showthread.php?t=2111487)
EXT4 Still Leads Over Btrfs File-System On Linux 3.8
[http://www.phoronix.com/scan.php?page=article&item=linux_38btrfs_ext4&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_38btrfs_ext4&num=1)

---

### Post by dabl on 2013-03-02
And from the BTRFS development team:

"BTRFS is stable on a stable system."

Which exactly reflects my experience, running a 2-drive BTRFS filesystem on a pair of WD-1002FAEX drives for two years now.  :)

---

### Post by Heeter on 2013-03-03
Thanks for your great responses, guys

Gonna try this btrfs, will stay away from the raid array.


Heeter

---

