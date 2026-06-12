---
title: "SD Card corrupted, but looks normal in parted"
date: 2016-06-18
forum: Hardware
---

### Post by ManiacDan on 2016-06-18
Morning everyone,

I woke up today to a message from my phone helpfully informing me that my SD card had become corrupt almost by magic overnight (I got the android 6 update from HTC and so far it's broken almost every major feature of the phone, but that's another story).

output of parted -l:


```
Model: SD SU64G (sd/mmc)
Disk /dev/mmcblk0: 63.9GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  63.9GB  63.9GB  primary               boot, lba
```





And the error message when I try to mount it:
```
Error mounting /dev/mmcblk0p1 at /media/maniacdan/FED4-AE7C: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/mmcblk0p1" "/media/maniacdan/FED4-AE7C"' exited with non-zero exit status 1:
stdout: `FUSE exfat 1.1.0
'
stderr: `ERROR: fsync failed: Input/output error.
'
```


Obviously this card can't be trusted, but my daughter's graduation was yesterday and my backup job runs Mondays so I'd like to recover those files if I can.  Any thoughts or tasks to perform?

Thanks!

**EDIT: For those with this same problem,** [this wonderful technibble post](https://www.technibble.com/guide-using-ddrescue-recover-data/) included all the information I needed, despite the weird windows context.  Just note that to get ddrescue you need to apt-get install gddrescue, from the universe repository.

---

### Post by ManiacDan on 2016-06-18
Update:  After looking for half an hour for ddrescue (for others with this problem, use apt-get install gddrescue, the g is in the package name but not the executable) I'm running a ddrescue now and may be able to dd the image onto a new sd card shortly.

---

### Post by ManiacDan on 2016-06-18
So this is interesting:

```

GNU ddrescue 1.19
Press Ctrl-C to interrupt
rescued:    63863 MB,  errsize:       0 B,  current rate:   13893 kB/s
   ipos:    63863 MB,   errors:       0,    average rate:   21224 kB/s
   opos:    63863 MB, run time:   50.15 m,  successful read:       0 s ago
Finished                                     

```

I was able to immediately mount the image and begin a backup.  The card is likely still hosed.

Now it's more academic.  What could cause a device to become unmountable but not have any errors from ddrescue?

---

### Post by sudodus on 2016-06-18
ddrescue can clone drives or partitions.

- Mounting a partition may not work if the file system is damaged, but this does not stop ddrescue for copying.

- ddrescue is better than standard methods to read, when some memory cells or sectors are are damaged and hard (but not impossible) to read, or maybe partly possible to read.

So it is a good idea to use ddrescue to clone, and then repair the file system on the cloned copy.

---

