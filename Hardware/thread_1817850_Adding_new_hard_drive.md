---
title: "Adding new hard drive"
date: 2011-08-03
forum: Hardware
---

### Post by leehach on 2011-08-03
Planning on adding a new SSD to my machine. Already read several great posts and other web pages with tips for minimizing disk writes, etc. I would like some input on the process for installing the new hard drive.

My goal is to have the root partition on a new 64 GB SSD and my /data partition on the old 500 GB hard drive. Currently I have / and /home as ext3 formatted 20 GB partitions (currently only using 12 GB and 5 GB, respectively). All data folders (Documents, Music, etc.) link to folders on a /data partition which will be on the HDD. I expect the speed advantage of using the SSD will mostly come from moving /, so what's the advantate of moving /home to the SSD or leaving it on the HDD?

Second, can I use parted to copy / from the HDD to the SSD? I know the simple answer is "yes", but please address the following complications: 

[LIST=1]
[*]/ is currently not bootable, as the old setup was a dual boot, and the actual boot partition was the Windows partition. (New setup will be single boot, and the Windows partition will be reclaimed for more useful stuff.)
[*]I would like the new partition to be ext4 in order to take advantage of TRIM support. Is there a way to change the current ext3 partition to ext4? Would I do this before, during, or after copying from the old HDD to new SSD?
[/LIST] 

Feel free to weigh in on anything you think I'm overlooking. I'm sure more questions will hit me later.

Partition table follows if useful or interesting.

```
Model: ATA SAMSUNG HD501LJ (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  49.4MB  49.3MB  primary   fat16
 2      50.3MB  10.8GB  10.7GB  primary   ntfs
 3      10.8GB  52.7GB  41.9GB  primary   ntfs            boot
 4      52.7GB  500GB   447GB   extended
 5      52.7GB  73.7GB  21.0GB  logical   ext3
 7      73.7GB  89.4GB  15.7GB  logical   ext3
 8      89.4GB  456GB   367GB   logical   ext3
10      456GB   477GB   20.9GB  logical   ext3
 9      477GB   498GB   21.0GB  logical   ext3
 6      498GB   500GB   2097MB  logical   linux-swap(v1)

```

---

### Post by movieman on 2011-08-03
If you copy over the ext3 partition can't you then do an in-place conversion of ext3 to ext4? I seem to remember they're compatible in that direction, but not going back from ext4 to ext3.

---

### Post by leehach on 2011-08-04
Yes, found instructions here for the ext3&#8594;ext4 migrations: [ConvertFilesystemToExt4]("https://help.ubuntu.com/community/ConvertFilesystemToExt4"). But how do I deal with question 1? If I stick in the SSD and install Ubuntu from scratch, it will be bootable. But the old / partition is not bootable, it chainloads from a bootable Windows partition. If I copy over the old / partition, so as to avoid a complete reinstall, can I just flag the partition as bootable?

---

