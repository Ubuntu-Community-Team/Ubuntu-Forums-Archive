---
title: "Partition table screwed up."
date: 2004-12-26
forum: Hardware &amp; Laptops
---

### Post by rohandhruva on 2004-12-26
Hello,

I know there are hundreds of questions about fixing the partition table. But mine, i suppose is a peculiar case. My disk structure is something like this:

1) Disk 1 - 10GB /dev/hda (partitioned into C:, ext3 for ubuntu hdinstall, lin-swap)
2) Disk 2 - 40GB /dev/hdb (partitioned into D:,E:, F: )

Windows, Knoppix HD-Install, and even distros like Suse can read data off /dev/hdc1(2,3..) and of course off /dev/hda. However the problem comes when installing distros. Whenever it comes to partitioning step, i *always* get a message saying "/dev/hdc: This disk is not initialised. Dow u want to format? This will erase entire disk" on RedHat and "This disk cannot be read. Please format it. Ignore this messgae if u are not planning to install Suse on this partition." on suse. Also, Partition Magic and QtParted cannot read the partitions on this disk. QtParted just hangs, and Partition Magic 6.0 on startup says that this disk need to be repaired. Sad I donot know whats up, but my guess is that it is due to corrupted partition table. Is there any way to repair the partition table, without damaging the data already stored on this disk? I mean, isnt it surprising that data can be read / written perfectly on this disk? What is the problem?

Also, in addition to this question, does QtParted support resizing and modifying data on a partition without damaging the data?

Rohan.

---

