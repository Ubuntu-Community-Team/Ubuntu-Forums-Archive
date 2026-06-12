---
title: "Auto-mounting NTFS external HDD"
date: 2008-03-23
forum: Hardware &amp; Laptops
---

### Post by Richard_Starkey on 2008-03-23
I'm having trouble auto-mounting my USB external NTFS partitions. I used ntfs-config - didn't work. Tried editing fstab manually - didn't work. What happens is that, on boot, the partitions disappear from 'computer' and the desktop. And it's not that the icon's aren't there as the respective mount points are empty. The partitions are also not corrupted as if I remove the mounting instructions from fstab and reboot the external drives, all the partitions reconnect like clockwork (read & write). I can also mount them after they 'disappear' by typing, for example, sudo mount /media/Data1, although the icons in 'computer' and on the desktop are still missing.
The two partitions I'm trying to auto-mount are, in this case, /dev/sdc3 ( Data 1) and /dev/sde1 (Data 2). As they are external, they change almost every time I boot so I used the partition's UUID's in fstab.
Note: I'm also auto-mounting my windows NTFS partition (/dev/sda2 or Local Drive) from my internal HDD and it works without a problem every time (read & write).

sudo fdisk -l is

```

hamishcook@hamishcook-laptop:~$ sudo fdisk -l
[sudo] password for hamishcook:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10db10da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         383     3076416   12  Compaq diagnostics
/dev/sda2             384        8216    62918572+   7  HPFS/NTFS
/dev/sda3   *        8217        9553    10739452+  83  Linux
/dev/sda4            9554        9729     1413720    5  Extended
/dev/sda5            9554        9729     1413688+  82  Linux swap / Solaris

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x9291b64a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      101586    51199312+   7  HPFS/NTFS
/dev/sdc2          101586      162531    30716469    7  HPFS/NTFS
/dev/sdc3          162617      969021   406428119    7  HPFS/NTFS

Disk /dev/sde: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xf7209963

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      969016   488384032+   7  HPFS/NTFS

```

and fstab is

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda2 :
UUID=829487F69487EB4D /media/Local_Drive ntfs defaults,locale=en_NZ.UTF-8 0 0
# Entry for /dev/sda3 :
UUID=37bb2981-d774-4bc2-9f45-926346f6681d / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=5f673455-78a7-4eb7-aaf5-60dc95b6cf6c none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0

UUID=2C243B28243AF504 /media/Data1 ntfs defaults,locale=en_NZ.UTF-8 0 0
UUID=F0CC831ACC82D9EC /media/Data2 ntfs defaults,locale=en_NZ.UTF-8 0 0

```

I'm new to linux and at a total loss. Any help would be hugely appreciated.

Thanks

---

