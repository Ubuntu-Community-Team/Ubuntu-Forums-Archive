---
title: "USB Hard Drive going read-only when corrupted files are found."
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by auraithx on 2007-08-01
My external USB FAT32 hard drive is turning read-only when it comes across a couple of corrupted files
here is the dmesg
```
glasgowm@glasgowm-desktop:~$ dmesg | tail
[283179.805634] SCSI device sdc: 488397168 512-byte hdwr sectors (250059 MB)
[283179.806739] sdc: Write Protect is off
[283179.806747] sdc: Mode Sense: 27 00 00 00
[283179.806750] sdc: assuming drive cache: write through
[283179.806756] sdc: sdc1
[283179.833451] sd 46:0:0:0: Attached scsi disk sdc
[283179.833521] sd 46:0:0:0: Attached scsi generic sg4 type 0
[283296.311770] FAT: Filesystem panic (dev sdc1)
[283296.311779] fat_get_cluster: invalid cluster chain (i_pos 0)
[283296.311784] File system has been set read-only
```

here's a fsck
```
glasgowm@glasgowm-desktop:~$ fsck.vfat -t -r /dev/sdc1
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  0:52/eb, 1:52/58, 2:61/90, 3:41/4d, 484:72/53, 485:72/44, 486:41/4f
  , 487:61/53
1) Copy original to backup
2) Copy backup to original
3) No action
? 3
No FSINFO sector
1) Create one
2) Do without FSINFO
? 1
FATs differ but appear to be intact. Use which FAT ?
1) Use first FAT
2) Use second FAT
? 1
/.Trash-glasgowm/Microsoft Visual Basic 6.0 Professional
  Contains a free cluster (3098657). Assuming EOF.
/.Trash-glasgowm/Incomplete
  Contains a free cluster (3268119). Assuming EOF.
/.Trash-glasgowm/PSXPSP.Pack.07.01.22-Torrentleech
  Contains a free cluster (2940686). Assuming EOF.
/.Trash-glasgowm/recycler
  Contains a free cluster (3057622). Assuming EOF.
/.Trash-glasgowm/Limewire Tunes
  Contains a free cluster (3080664). Assuming EOF.
/.Trash-glasgowm/South Park/SouthPark/Season 2
  Contains a free cluster (6101253). Assuming EOF.


```
It found those results within the first few minutes and then kept going for 3 hours so I stopped it (ctrl+C)

---

### Post by NickArgyle on 2007-08-01
My external hd has done the same on multiple installs of feisty on different pcs. This should certainly be fixed. Luckily this hasn't happend yet on my laptop.

---

### Post by auraithx on 2007-08-01
There must be some command that lets me override this read-only thing and delete the .Trash-glasgowm..

this has also made the drive not work on PCs/Macs - I'm assuming it's because they see the corrupted files and refuse/cant read the drive


Arrrgg!!!!
```
glasgowm@glasgowm-desktop:~$ sudo rm -r '/media/disk-1/.Trash-glasgowm'
rm: cannot lstat `/media/disk-1/.Trash-glasgowm/Microsoft Visual Basic 6.0 Professional': Input/output error

```

---

### Post by auraithx on 2007-08-03
bump

---

### Post by auraithx on 2007-08-09
bumpy

---

