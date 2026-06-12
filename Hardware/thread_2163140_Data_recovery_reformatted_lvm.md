---
title: "Data recovery reformatted lvm"
date: 2013-07-17
forum: Hardware
---

### Post by Shaggin Shea on 2013-07-17
I have a computer with 2 hard drives that were formated lvm. I reformatted (again with LVM) and reinstalled a new LVM but due to brainfart only later realized I had a file on the old LVM partition (same disks).

I was looking at this guide [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) but there are so many options I am overwhelmed.

I don't have any files to backup on the new LVM as it is a fresh install.

fyi The file I am looking to restore is either a zip of pictures or a folder of pictures.

> [h=2]Lost Partition[/h] If you made a  mistake while partitioning and the partition no longer appears in the  partition table, so long as you have not written data in that space, all  your data is still there.

Since I wrote data via a new partion does that mean my partition is no longer there (but is the data still on the drive?Recoverable?)

> Then, use the rescue option: 

rescue START END 
where  Start is the area of the disk where you believe the partition began and  END is its end.  If parted finds a potential partition, it will ask you  if you want to add it to the partition table.

How would I have any idea on the start/end?

Should I be looking into recovering the partition or using something that scans the drive?

P.S. The drives (LVM) are not failing. Just my mind ;)

---

