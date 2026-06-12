---
title: "Mounting NTFS for each session?"
date: 2007-07-30
forum: Hardware &amp; Laptops
---

### Post by mrfraser89 on 2007-07-30
Hey guys,  my hard drives mount without a problem, however i have Exaile set to play my music directory off my windows hard drive, unfortunately if the drive doesnt mount on the system load up Exaile has to build the playlist each time...

how can i mount a certain ntfs partition on system logon?

---

### Post by erfahren on 2007-07-30
edit your /etc/fstab

see [the wiki entry](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only) and the [psychocats tutorial](http://www.psychocats.net/ubuntu/mountwindows)

I mounted my FAT32 data partition that way, but it was already listed in there. I had to comment that line out before I made the new entry:

my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=1c5b88a9-a1c4-47b8-933e-bf940fd9d8d5 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=f7b582e1-27d1-4416-807b-1b5ed1d362ec /home           ext3    defaults        0       2
# /dev/sda1
# UUID=7004581F16D9B5D2 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
# UUID=A4E40FFDE40FD10A /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
# UUID=3CA5-B33D  /media/sda3     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=78d2f666-d3fc-4ec7-b515-b5a1414fbe5e none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
# Manual Additions
/dev/sda3  /mnt/D     vfat    iocharset=utf8,umask=000     0       0    

```

it was listed as /media/sda3 and I commented out that entry and re-added it at the bottom. (I commented out my ntfs Vista and recovery partition just because I don't need to see them.) Oh, and I made the directory "/mnt/D" for its mount point.

---

### Post by aysiu on 2007-07-30
You'll have to add it to your /etc/fstab

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows) should help.

---

