---
title: "new hdd alignment issue, parted and fdisk aligning differently"
date: 2019-01-05
forum: Hardware
---

### Post by wyrm82 on 2019-01-05
Hi there,
I got a new hdd for my NAS setup (Odroid HC2), WD40EFRX. That's a 4TB disk with Advanced Format support. When making a new partition with Ubuntu 18.04, I stumbled upon error messages saying it is not properly aligned.
Funny thing is that when I align it with fdisk, parted tells it is not properly aligned. When I used parted to align, fdisk complains the same.
I am not linux expert so I hope someone please help me with easy steps.

```

(parted) mkpart primary ext4 0% 100%
(parted) print
Model: JMicron  (scsi)
Disk /dev/sda: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags:

Number  Start   End     Size    File system  Name     Flags
 1      33.6MB  4001GB  4001GB  ext4         primary

(parted) align-check opt 1
1 aligned

root@odroid:~# fdisk -l

...

Disk /dev/sda: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt
Disk identifier: FC9921D5-BD2C-4EFA-9BD4-37E9B6B4F7ED

Device     Start        End    Sectors  Size Type
/dev/sda1  65535 7814000189 7813934655  3.7T Linux filesystem

Partition 1 does not start on physical sector boundary.

```


```

root@odroid:~# fdisk -c -u /dev/sda

Welcome to fdisk (util-linux 2.31.1).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.


Command (m for help): n
Partition number (1-128, default 1):
First sector (34-7814037134, default 2048):
Last sector, +sectors or +size{K,M,G,T,P} (2048-7814037134, default 7814037134):

Created a new partition 1 of type 'Linux filesystem' and of size 3.7 TiB.

Command (m for help): p
Disk /dev/sda: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
Disklabel type: gpt
Disk identifier: FC9921D5-BD2C-4EFA-9BD4-37E9B6B4F7ED

Device     Start        End    Sectors  Size Type
/dev/sda1   2048 7814037134 7814035087  3.7T Linux filesystem

Command (m for help): w
The partition table has been altered.
Calling ioctl() to re-read partition table.
Syncing disks.

root@odroid:~# parted /dev/sda
GNU Parted 3.2
Using /dev/sda
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) align-check opt 1
1 not aligned

```

So I did some searching... and found [this]("https://rainbow.chard.org/2013/01/30/how-to-align-partitions-for-best-performance-using-parted/") post and checked my alignment parameters.

```

root@odroid:~# cat /sys/block/sda/queue/optimal_io_size
33553920
root@odroid:~# cat /sys/block/sda/queue/minimum_io_size
4096
root@odroid:~# cat /sys/block/sda/alignment_offset
0
root@odroid:~# cat /sys/block/sda/queue/physical_block_size
4096

```

And apparently my optimal IO size is not divided by my physical block size.
I guess this might be the source of the problem, or I am getting this completely wrong.

So what is the proper way to align my disk in this case?
Thanks.

---

### Post by oldfred on 2019-01-05
Start at 2048 is the standard.

Old versions of fdisk did not support gpt, so we used gdisk.
       [http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

Every writeable partitions start must be divisible by 8.
see posts by Rod  Smith (author of gdisk).
[https://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted](https://askubuntu.com/questions/201164/proper-alignment-of-partitions-on-an-advanced-format-hdd-using-parted)
      
 [https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/index.html)

---

