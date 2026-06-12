---
title: "Expanding a partition with raid on it and other issues"
date: 2009-09-17
forum: Hardware
---

### Post by bradtem on 2009-09-17
Due to changing drives over time, I have a 3x480g raid-5 on 3 disks:
[LIST=1]
[*]2 1TB drives with 730gb partitions on them for RAID
[*]One 750gb disk with a 480gb partition on it for RAID but 250gb empty space after it
[/LIST]

However, due to older drives the RAID components are 480gb, as that was the size of the smallest one, but as noted there is now 250gb of empty space after the RAID.   So it should be possible to just expand that partition, and ask the raid to --grow size=max to notice it now has 3 larger partitions and have at them.

However, the tools like parted will not resize a partition with a raid in it.   Further, this raid has metadata 0.9 (the default for mdadm creation) which stores the superblock at the end, and I presume it might not find it in a newly grown partition even if I do it by deleting and recreating the larger partition with fdisk.

So is there a howto on expanding a partition with a RAID component on it into empty space?

Of course, there is the old fashioned way -- fail out the partition, delete it, and add it again.  This will cause the RAID to rebuild, which takes many hours and also incurs some risk if there is some hidden error on the other two drives or a random bit error occurs.  It should work but it is best not to do this if you don't need to do this.

(In general, I think it would also be good if the raid subsystem had a method for replacing a **working** drive rather than failing it out and having a new drive or hot spare take over.   It seems that when replacing a working drive, the system should be able to do the rebuild onto the new drive mostly by copying (while still online) but doing any new writes to the new drive.  In that way, if an error is found on one of the other drives during this transfer, the data can still be recovered from the to-be-removed drive.    Is this possible, or something planned for the future?)

---

