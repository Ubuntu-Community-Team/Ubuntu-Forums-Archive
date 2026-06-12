---
title: "SDB: Could this be a zero-length partition?"
date: 2012-08-16
forum: Hardware
---

### Post by jiapei100 on 2012-08-16
Hi, all:

In fact, I'm continuing a closed topic, which can be found at
[http://ubuntuforums.org/showthread.php?p=12175678](http://ubuntuforums.org/showthread.php?p=12175678)


1) 
```
pei@pei-GA-870A-UD3:/dev$ ls -l sd*
brw-rw---- 1 root disk 8,  0 Aug 15 17:57 sda
brw-rw---- 1 root disk 8,  1 Aug 15 17:55 sda1
brw-rw---- 1 root disk 8,  2 Aug 15 17:57 sda2
brw-rw---- 1 root disk 8,  5 Aug 15 17:55 sda5
brw-rw---- 1 root disk 8,  6 Aug 15 17:57 sda6
brw-rw---- 1 root disk 8, 16 Aug 15 17:57 sdb
brw-rw---- 1 root disk 8, 17 Aug 15 17:55 sdb1
brw-rw---- 1 root disk 8, 48 Aug 15 18:18 sdd
brw-rw---- 1 root disk 8, 49 Aug 15 18:18 sdd1
brw-rw---- 1 root disk 8, 64 Aug 16 01:04 sde
```
As you can see, only sde, no sde1 .

2)
```
pei@pei-GA-870A-UD3:~/Desktop$ sudo dd if=/dev/sde of=/dev/null count=8
dd: reading `/dev/sde': Input/output error
0+0 records in
0+0 records out
0 bytes (0 B) copied, 16.2421 s, 0.0 kB/s
```


3)
```
pei@pei-GA-870A-UD3:~/Desktop$ sudo smartctl -d scsi -T permissive -a /dev/sde
smartctl 5.41 2011-06-09 r3365 [i686-linux-3.2.0-29-generic-pae] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net

Vendor:               Generic 
Product:              Storage Device  
Revision:             0.00
User Capacity:        16,005,464,064 bytes [16.0 GB]
Logical block size:   512 bytes
scsiModePageOffset: response length too short, resp_len=4 offset=4 bd_len=0
>> Terminate command early due to bad response to IEC mode page

Error Counter logging not supported
scsiModePageOffset: response length too short, resp_len=4 offset=4 bd_len=0
Device does not support Self Test logging
```



Please, help....


Cheers
Pei

---

### Post by spjackson on 2012-08-16
/dev/sde appears to be a 16GB disk without a partition table. Check what gparted says or this:
```

sudo fdisk -l /dev/sde

```

---

### Post by TonyDeWittePony on 2012-08-16
I started the original thread, and the only way that solved things was when they replaced both hard drives. No more problems ever since. Hope your problem is a different one, as I lost a bunch of data and learnt a valuable lesson.

---

### Post by jiapei100 on 2012-08-16
Replace both hard drives?
Do you mean that I need to return the SD Cards and get some other ones from the store?


Cheers
Pei



> **TonyDeWittePony said:**
> I started the original thread, and the only way that solved things was when they replaced both hard drives. No more problems ever since. Hope your problem is a different one, as I lost a bunch of data and learnt a valuable lesson.

---

### Post by jiapei100 on 2012-08-16
Yes, spjackson.
You are absolutely correct. There is no partition table on that SD card. It's probably me who delete/remove the partition.... It used to have the partition. Even now, I'm not able to copy/create a partition using testdisk.


Any further suggestions?

Thank you very much.


Best Regards
Pei



> **spjackson said:**
> /dev/sde appears to be a 16GB disk without a partition table. Check what gparted says or this:
```

sudo fdisk -l /dev/sde

```

---

### Post by spjackson on 2012-08-16
Can you create a partition with gparted or fdisk? If not I don't know what else you can do about it.

---

