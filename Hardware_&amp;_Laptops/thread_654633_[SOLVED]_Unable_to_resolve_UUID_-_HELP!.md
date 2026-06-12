---
title: "[SOLVED] Unable to resolve UUID - HELP!"
date: 2007-12-31
forum: Hardware &amp; Laptops
---

### Post by Salpiche on 2007-12-31
So I turned off my computer last night and upon boot this morning it gave me an error > /dev/sda2: clean, 34014/3948544 files, 4020813/7885080 blocks (check after next mount)
fsck.ext3: Unable to resolve 'UUID=1afaaf75-96df-46e2-9305-7f30823619d2'

not mounting my /home partition (using root part @ this time), and swap partition

Notes:
I have been running this install since release date (7.10 Gutsy)

sda1 = Winxp
sda2 = /home
sda3 = /root

sdb1 = storage
sdb3 = swap


now everything was working fine last night, why would it do this? and how can I recover my system?

just in case: 
here is my 

fdisk
```
root@Taino:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xe6e883f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4779    36129208+   7  HPFS/NTFS
/dev/sda2            6166       10337    31540320   83  Linux
/dev/sda3            4780        6165    10478160   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
240 heads, 63 sectors/track, 7753 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x009d72e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7612    57546688+   7  HPFS/NTFS
/dev/sdb3            7613        7753     1065960   82  Linux swap / Solaris

```

checkfs
```
Log of fsck -C -R -A -a 
Mon Dec 31 09:44:30 2007

fsck 1.40.2 (12-Jul-2007)
/dev/sda2: clean, 34014/3948544 files, 4020813/7885080 blocks (check after next mount)
fsck.ext3: Unable to resolve 'UUID=1afaaf75-96df-46e2-9305-7f30823619d2'

fsck died with exit status 8

Mon Dec 31 09:44:31 2007
```

and my 
fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=9648bf58-be95-420c-80a1-5a2e2b00a883 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=821dbb65-202f-4196-9414-6d7f8ab2f986 /home           ext3    defaults        0       2
# /dev/sda1
# /dev/sdb1
# /dev/sdb3
UUID=1afaaf75-96df-46e2-9305-7f30823619d2 /media/sdb3     ext3    defaults        0       2
# /dev/sdb2
UUID=8f7411e7-b452-4a7e-907d-f8df5d890880 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/sda1   /media/sda1   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sdb1   /media/sdb1   ntfs-3g  defaults,locale=en_US.utf8    0    0

```

is there anything else?

---

### Post by taurus on 2007-12-31
> **Salpiche said:**
> So I turned off my computer last night and upon boot this morning it gave me an error 

not mounting my /home partition (using root part @ this time), and swap partition

Notes:
I have been running this install since release date (7.10 Gutsy)

sda1 = Winxp
sda2 = /home
sda3 = /root

sdb1 = storage
sdb3 = swap

now everything was working fine last night, why would it do this? and how can I recover my system?

just in case: 
here is my 

fdisk
```
root@Taino:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0xe6e883f9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4779    36129208+   7  HPFS/NTFS
/dev/sda2            6166       10337    31540320   83  Linux
/dev/sda3            4780        6165    10478160   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
240 heads, 63 sectors/track, 7753 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x009d72e9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7612    57546688+   7  HPFS/NTFS
[COLOR="Blue"]/dev/sdb3            7613        7753     1065960   82  Linux swap / Solaris[/COLOR]

```

checkfs
```
Log of fsck -C -R -A -a 
Mon Dec 31 09:44:30 2007

fsck 1.40.2 (12-Jul-2007)
/dev/sda2: clean, 34014/3948544 files, 4020813/7885080 blocks (check after next mount)
fsck.ext3: Unable to resolve 'UUID=1afaaf75-96df-46e2-9305-7f30823619d2'

fsck died with exit status 8

Mon Dec 31 09:44:31 2007
```

and my 
fstab
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=9648bf58-be95-420c-80a1-5a2e2b00a883 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=821dbb65-202f-4196-9414-6d7f8ab2f986 /home           ext3    defaults        0       2
# /dev/sda1
# /dev/sdb1
# /dev/sdb3
[COLOR="Blue"]UUID=1afaaf75-96df-46e2-9305-7f30823619d2 /media/sdb3     ext3    defaults        0       2[/COLOR]
# /dev/sdb2
UUID=8f7411e7-b452-4a7e-907d-f8df5d890880 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/sda1   /media/sda1   ntfs-3g  defaults,locale=en_US.utf8    0    0
/dev/sdb1   /media/sdb1   ntfs-3g  defaults,locale=en_US.utf8    0    0

```

is there anything else?

Isn't /dev/sdb3 your swap but you have it mount as ext3?  What happens if you change it to

```

UUID=1afaaf75-96df-46e2-9305-7f30823619d2   none   swap   sw   0   0
```

---

### Post by Salpiche on 2007-12-31
Thanks! I didn't notice that.. changed and rebooting, lets see!!!!



:lolflag:

---

### Post by Salpiche on 2007-12-31
> **taurus said:**
> Isn't /dev/sdb3 your swap but you have it mount as ext3?  What happens if you change it to

```

UUID=1afaaf75-96df-46e2-9305-7f30823619d2   none   swap   sw   0   0
```


Thanks that did it!

---

