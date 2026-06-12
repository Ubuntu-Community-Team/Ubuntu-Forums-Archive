---
title: "Hard Drive Parititon / Format Issues"
date: 2009-01-18
forum: Installation &amp; Upgrades
---

### Post by johnschlafer on 2009-01-18
Hello,

I recently installed a new Western Digital 160 Gb hard drive into my Dell Inspiron 1450 laptop. When I installed Windows XP SP2 I created 2 partitions on the hard drive. The first partition is ~120Gb and I formatted the partition and installed Windows XP on it. The second partition is ~40 GB. It is unformatted, and I would like to install Ubuntu on it. 

When I go to install Ubuntu 8.10 by running the installation CD the partitioner will not let me install Ubuntu on just the unformatted ~40 GB partition. 

My question is: How do I get Ubuntu to install on the 40 GB unformatted partition of my hard drive? More information on the options the partitioner gives me is below.

Thanks for any help!
John




The partitioner gives me 4 options and none allow me to install just on the unformatted partition. What the four options give me are:

1) "Guided - resize SCSI1 (0,0,0), Partition #1 (sda)and use free space" - This shows splitting the first partition into 68.4 and 51.3 GB sections and not using the unformatted partition.

2) "Guided - use entire disk" - This uses the entire disk including the second ~40 GB partition.

3) "Guided - use the largest continuous free space" - This also uses the entire disk including the second ~40 GB partition.

4) "Manual" - This only allows me to use the entire disk, including the second ~40 GB partition. I am unable to figure out how to make any adjustments under this setting.

---

### Post by aheckler on 2009-01-18
You need to use the Manual setting. Select the 40GB partition, use / as the mount point, ext3 as the FS type, and check "Format". Just be sure not to have "Format" check for your Windows partition and you should be fine.

---

