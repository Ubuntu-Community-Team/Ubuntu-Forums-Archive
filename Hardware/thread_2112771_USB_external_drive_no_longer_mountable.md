---
title: "USB external drive no longer mountable"
date: 2013-02-05
forum: Hardware
---

### Post by dayers on 2013-02-05
I have been using a 64G usb stick that used to mount normally, but now it will not mount because it apparently has become write-protected.

I more or less randomly gathered some information (below) but I need some help. I hope someone can point me in the right direction.

From blkid:

/dev/sdb: UUID="f6dab663-bab4-44d2-8561-949b6637a9f8" TYPE="ext3" 

dave@homebase:~$ sudo mount /archive
[sudo] password for dave: 
mount: block device /dev/sdb is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sdb,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dave@homebase:~$ dmesg|tail
[90124.052194] sd 18:0:0:0: [sdb] Assuming drive cache: write through
[90124.207303] sd 18:0:0:0: [sdb] No Caching mode page present
[90124.207308] sd 18:0:0:0: [sdb] Assuming drive cache: write through
[90124.297279]  sdb: unknown partition table
[90382.466773] EXT3-fs (sdb): recovery required on readonly filesystem
[90382.466778] EXT3-fs (sdb): error: write access unavailable, cannot proceed
...
dave@homebase:~$ 

From fdisk -l:

Disk /dev/sdb: 65.5 GB, 65451982848 bytes
64 heads, 32 sectors/track, 62419 cylinders, total 127835904 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table


Thanks,

Dave

---

### Post by ahallubuntu on 2013-02-05
~

---

### Post by dayers on 2013-02-06
Thanks for your response.

On another Win7 machine, the USB stick was not recognized every time it was plugged in.

On another port on the original Win7 machine, it still could not be mounted.

And then it could... I'm chasing my tail again. Later.

---

### Post by dayers on 2013-02-07
Just to close the loop, I purchased a new USB stick, formatted it, and had no trouble mounting and using it. Problem may not have been "solved," but at least I am going again.

Thanks for your help.

---

