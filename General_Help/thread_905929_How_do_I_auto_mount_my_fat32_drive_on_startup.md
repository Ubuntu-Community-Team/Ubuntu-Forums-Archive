---
title: "How do I auto mount my fat32 drive on startup"
date: 2008-08-30
forum: General Help
---

### Post by souljahh2050 on 2008-08-30
I wold like to autount /dev/sda5. /media/STORAGE How would I add that to fstab? Everytime I try I get an error.

Thx,




Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb90883c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5170    41527993+   7  HPFS/NTFS
/dev/sda2           11356       12121     6152895   83  Linux
/dev/sda3           12122       12161      321300   82  Linux swap / Solaris
/dev/sda4            5171       11355    49681012+   f  W95 Ext'd (LBA)
/dev/sda5            5171       11355    49680981    b  W95 FAT32

-------------------------------------------------------------------------------------
--------------------------------------------------------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=36902e9b-19f0-4e10-8e59-d1a6e531f58f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=8885d0bc-c6ad-4b48-943d-8dd3edcdf8e1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Taxman415a on 2008-08-31
What errors do you get? Can you mount it manually, with say ```
sudo mount /dev/sda5 /media/storage
```

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
gives a pretty good introduction to setting up your fstab file.

---

### Post by souljahh2050 on 2008-08-31
When I try to mount it I get this error.

mount: mount point /media/storage does not exist

---

### Post by Too Late on 2008-08-31
The directory 'storage' (or 'STORAGE', case matters) must exist before mounting. To create that directory, type:
```
sudo mkdir /media/storage
```

---

