---
title: "Mounting an external drive using UUIDs"
date: 2007-05-09
forum: Hardware &amp; Laptops
---

### Post by vs292 on 2007-05-09
Hey guys,

I read [this](http://ubuntuforums.org/showthread.php?t=384006) thread the other day as I have the same problem and tried using the advice there to sort it out, but I can't seem to get it to work.


I ran ls /dev/disk/by-uuid/ and figured out that the drive I want to mount in /media/MyBook is called D558-7E0A.

I then added 
```
UUID=D558-7E0A /media/MyBook	vfat	rw,uid=1001,noexec,nodev,utf8	0	0
``` to /etc/fstab and it doesn't seem to work, even on reboot.

I also tried manually mounting it using 
```
sudo mount -t vfat -o rw,nodev,noexec,uid=1001 /dev/sdd /media/MyBook
```
and get this error:

```
*****@*****:~$ sudo mount -t vfat /dev/sdd /media/MyBook
mount: wrong fs type, bad option, bad superblock on /dev/sdd,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

What am I doing wrong? :s:

Any help will be greatly appreciated!

Thanks.

PS: This is my /etc/fstab as it stands now:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=8ab38a86-60c7-493b-a964-3ac1438431e6 /               reiserfs notail          0       1
# /dev/sda7
UUID=4be776fa-c5cb-48c0-b60c-a0c5b916ec12 /home           reiserfs defaults        0       2
# /dev/sda1
UUID=6404C55404C52A3E /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=4629-209B  /media/sda2     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=3aef1a51-c7a4-46e9-a7c6-61f2cdf9d43e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sdb        /media/floppy0  auto    rw,user,noauto  0       0
# MyBook
UUID=D558-7E0A /media/MyBook	vfat	rw,uid=1001,noexec,nodev,utf8	0	0

```

and this is the output from ls /dev/disk/by-uuid/
```

*****@*****:~$ ls /dev/disk/by-uuid/
3aef1a51-c7a4-46e9-a7c6-61f2cdf9d43e  55D123D9E79ABF54
44CC02A4CC028FFA                      6404C55404C52A3E
4629-209B                             8ab38a86-60c7-493b-a964-3ac1438431e6
4be776fa-c5cb-48c0-b60c-a0c5b916ec12  D558-7E0A

``` 

and this is fdisk -l
```

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       60801   488384001    c  W95 FAT32 (LBA)

```

---

