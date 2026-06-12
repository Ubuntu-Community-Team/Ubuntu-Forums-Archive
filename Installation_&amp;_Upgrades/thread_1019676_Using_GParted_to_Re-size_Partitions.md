---
title: "Using GParted to Re-size Partitions"
date: 2008-12-23
forum: Installation &amp; Upgrades
---

### Post by maporojo on 2008-12-23
I am a Linux newbie and by no means a computer geek. I have a dual boot machine with a ~38GB HDD (~27GB for Windows XP SP2 and ~11GB for Ubuntu Hardy Heron).

This is my goal:
- to increase the size of the partition with XP by ~1GB (by decreasing the size of the partition with Hardy Heron by ~1GB)

This is what I did:
- I used GParted from the Ubuntu Live CD to re-size the Linux partition to ~9GB thereby freeing ~1GB (I did not touch the swap partition)
- I right-clicked on the newly unallocated space of about ~1GB and formatted it to NTFS

Observations:
- I see a new drive of ~1GB, as expected, listed in the explorer tree after rebooting XP

This is what I need help with:
- how to add the ~1GB NTFS partition to the ~27GB NTFS partition so that when I boot windows I actually see only one drive of ~28GB.

NB-I have read about nightmares that people have had after using Partition Magic 8.0 so I have avoided using it.

---

### Post by Idefix82 on 2008-12-23
Delete the 1GB NTFS partition again, make sure that the unallocated space of 1GB is to the right of the XP partition and resize the XP partition to increase it by 1GB.

---

### Post by maporojo on 2008-12-23
I was able to delete the ~1GB partition after right-clicking the swap partition and choosing "Swapoff". I restored the swap partition to the "Swapon" option that it had before.

I moved the unallocated space (by fiddling with the "Free Space Preceding" and "Free Space Following" values) so that it is to the right of the XP partition and to the left of the Ubuntu files.

Thanks.

---

