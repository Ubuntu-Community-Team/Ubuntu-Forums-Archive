---
title: "External Hard Drive Problems"
date: 2010-01-08
forum: Hardware
---

### Post by buster2209 on 2010-01-08
I'm having such a headache with my external hard drive!

I've formatted the thing a million times but I STILL get this persistent problem.

Moving files ***to*** my external HD ***from*** my internal HD is fine, there is never a problem but when I want to move a file ***from*** my external HD ***to*** my internal HD, I usually get an input/output error, or, if I'm really lucky, I get a transfer speed of < 1.0 mb/s!

Here is my fdisk -l output;

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x38000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6180    49640818+   7  HPFS/NTFS
/dev/sda2            6181       38913   262927822+   5  Extended
/dev/sda5            6181       37589   252292761   83  Linux
/dev/sda6           37590       38913    10634998+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0006dec5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001   83  Linux
```

and here is my etc/fstab output;

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda5
UUID=9a9ffc9a-854d-4532-b1c7-36fd1947064c /               ext3    relatime,errors=remount-ro 0       1

# /dev/sda6
UUID=15ad1e92-254f-416c-aa78-4185303f9ae5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I've also tried using a different USB cable to see if that was the problem but that didn't sort it either.  The HD isn't that old, probably about a year so I don't think it's broken.

I'm using Ubuntu Hardy and the drive has worked fine for about 6 months.

Any help would be greatly appreciated!!!

---

### Post by buster2209 on 2010-01-09
bump

---

### Post by mk1w86 on 2010-01-09
What filesystem are you using on the external drive?:-s

---

### Post by buster2209 on 2010-01-09
> **mk1w86 said:**
> What filesystem are you using on the external drive?:-s

ext2.  I use Linux exclusively so don't need to bother with NTFS.

Is there a better format to use?

---

### Post by mk1w86 on 2010-01-10
> Is there a better format to use? 

Although not necessarily a better filesystem, you could try NTFS or FAT32 and see if you have the same problem.  You could even try ext3 although it is essentially ext2 with a journal. ;)

---

### Post by buster2209 on 2010-01-11
> **mk1w86 said:**
> Although not necessarily a better filesystem, you could try NTFS or FAT32 and see if you have the same problem.  You could even try ext3 although it is essentially ext2 with a journal. ;)

Changed it to FAT32 and so far so good.

If this doesn't work, I'm cashing in on the 5yr warranty I have on the external HD! ;)

---

