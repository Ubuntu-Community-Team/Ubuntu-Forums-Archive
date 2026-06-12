---
title: "Can't grow EXT4 Partition"
date: 2014-07-05
forum: Hardware
---

### Post by electricmaster on 2014-07-05
I am trying to grow my ext4 partition to fill the adjacent unallocated space using GParted on an Ubuntu live CD. My drive's setup looks like this:
[ATTACH=CONFIG]254500[/ATTACH]
When I go to resize the paritition to cover the unallocated space, it shows like the space isn't there:
[ATTACH=CONFIG]254501[/ATTACH]
I'm not sure about how to go about resizing the partition and I am wondering if anyone else knows how to do this. I would prefer to resize the partition without reformatting or losing any data. It is my understanding that both the partition and filesystem needs to be resized seperately. As I'm not completely sure what I'm doing, I would appreciate it if someone would walk me through the process.

fdisk returns the following about my hardrive:
```
Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b531b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2046   136970239    68484097    5  Extended
/dev/sdb2       234985472   308385791    36700160    7  HPFS/NTFS/exFAT
/dev/sdb3       308385792   312580095     2097152   82  Linux swap / Solaris
/dev/sdb5            2048   136970239    68484096   83  Linux

```

Thanks in advanced.

---

### Post by Dennis N on 2014-07-05
sdb5 must be "inside" sdb1 (sdb5 is a logical partition created in the extended partition sdb1). It can be no larger than sdb1. So, you have to first resize sdb1 into the unallocated space. Then you should be able to resize sdb5.

---

