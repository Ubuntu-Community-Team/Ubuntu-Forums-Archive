---
title: "Hard disk failure"
date: 2007-08-15
forum: Hardware &amp; Laptops
---

### Post by mental_drummer on 2007-08-15
Please help ubuntu gurus - you havnt failed me yet!
So i have edgy and windows dual booting on my primary hard drive. On a slave i have my main home directory. this slave hard disk seems to have some problem and cannot mount now

```
niall2@sonofyashmak:~$ sudo mount /dev/sdb1
Password:
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

niall2@sonofyashmak:~$ dmesg | tail
[ 7062.635428] end_request: I/O error, dev sdb, sector 156248184
[ 7062.635811] sd 0:0:1:0: SCSI error: return code = 0x00040000
[ 7062.635815] end_request: I/O error, dev sdb, sector 156248184
[ 7343.988736] sd 0:0:1:0: SCSI error: return code = 0x00040000
[ 7343.988743] end_request: I/O error, dev sdb, sector 0
[ 7343.988746] printk: 5470 messages suppressed.
[ 7343.988749] Buffer I/O error on device sdb, logical block 0
[ 7517.379064] sd 0:0:1:0: SCSI error: return code = 0x00040000
[ 7517.379070] end_request: I/O error, dev sdb, sector 65
[ 7517.379281] EXT2-fs: unable to read superblock
niall2@sonofyashmak:~$ 

```

i have no idea what dmesg is saying! 
I cant still boot as the operating system is on the other drive. The BIOS can see both hard disks so i dont think its totally dead.

So i heard testdisk is good for this kind of thing. However when I run it and select /dev/sbd to "analyse" it cannot find any partitons and return "Partition: read error" I scan it and the it comes back with "Stucture ok" but there are no partitions listed.
Incidentally the hard disk is detected as 79GB when it should be 80 - i dont know if this is a significant difference.

I also tried gpart and I get this error
```
niall2@sonofyashmak:~$ gpart /dev/sdb1

*** Fatal error: cannot get sector size on dev(/dev/sdb1).

```

Please please can anyone help me? Im begging!
thanks

---

### Post by psusi on 2007-08-15
The disk is screwed.

---

