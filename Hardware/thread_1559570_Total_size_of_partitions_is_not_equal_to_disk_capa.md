---
title: "Total size of partitions is not equal to disk capacity"
date: 2010-08-23
forum: Hardware
---

### Post by larikot on 2010-08-23
Hi all,

I've just bought a new external disk of 1TB :
```

% sudo fdisk -l

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x017c233f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2    23301691   734003235    7  HPFS/NTFS
/dev/sdb2        23301692    28294911   157286430   83  Linux
/dev/sdb3        28294912    31008336    85472887+   7  HPFS/NTFS

```

I have created 3 partition with fdisk entering size like this :
partition 1 : +700G
partition 2 : +150G
partition 3 : I let the last cylinder, so until the end of disk

The problem is, the total size of the 3 partitions is not equal to the disk capacity :
partition 1 : 701 GB
partition 2 : 142 GB
partition 3 :  82 GB
```

%df -h
/dev/sdb1             701G   20G  681G   3% /media/part1
/dev/mapper/udisks-luks-uuid-f151f31a-2887-40b1-a829-eac0497b315e-uid1000
                      149G  188M  142G   1% /media/back1
/dev/mapper/udisks-luks-uuid-f03f59ed-aa51-4ef2-961b-49c344af2c58-uid1000
                       82G   68M   82G   1% /media/back2

```

The 3 partition's size : 932 GB wich is less than 1000.2 GB

Where are the missing 68 GB ?
Maybe I should redo the partitions with other values to fit perfectly the disk capacity ???

thanks.

---

### Post by Fafler on 2010-08-23
The partitions span all available cylinders. Nothing wrong there. The issue is that harddrive manufactures and the rest of the world counts diskspace differently. Seagate says 1 kb is 1000 bytes, and mathematically, they are correct, but common practice has always been that it's 1024 bytes, because it fits better with the way computers cound in power of two. So the 1000 gb on the label of drive pretty much adds up as the 932 gb you're getting. You also loose some space to filesystem data etc.

---

### Post by srs5694 on 2010-08-23
There is some movement toward clarifying the matter by enforcing the use of "kilo-", "mega-", "giga-", and so on prefixes, and abbreviations such as KB, MB, GB, etc., for power-of-10 units. That is, "1 megabyte" is 1,000,000 bytes (that is, 10^6 bytes). This is the way drive manufacturers label things. New power-of-2 units have new prefixes and abbreviations: "kibi-", "mebi-", "gibi-", and so on, with abbreviations of KiB, MiB, GiB, and so on. By these measures, 1 mebibyte is 1,048,576 bytes (that is, 10^20 bytes). Not all software and documentation has caught up with this new standard, and it does have the disadvantage of requiring people to understand more; but it is much clearer and more precise, and it enables selection of units that are appropriate for different purposes. See [this page](http://physics.nist.gov/cuu/Units/binary.html) for more information.

---

