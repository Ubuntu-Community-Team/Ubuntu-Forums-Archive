---
title: "unable to mount volume"
date: 2008-10-07
forum: General Help
---

### Post by Julius1988 on 2008-10-07
for some odd reason sda1 is not mounted dnt know why?i never had problems with it before

output of
/etc/fstab
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda9
UUID=f72d3d79-a4aa-4825-82dd-8b0c7bf79c04 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda10
/dev/sda5 /media/sda5 ntfs defaults,umask=007,gid=46 0 0 
/dev/sda6 /media/sda6 ext3 defaults 0 1
/dev/sda7 /media/sda7 vfat defaults,umask=007,gid=46 0 0 
/dev/sda8 /media/sda8 ntfs defaults,umask=007,gid=46 0 0
/dev/sda1 /media/sda1 ntfs defaults,umask=007,gid=46 0 0
UUID=d2973430-107b-468d-9eb2-93267f184bb4 none            swap    sw              0       0
/dev/sdb1       /media/pen-drive   vfat,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom2   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


```

output of
```


sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc164c164

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6374    51199123+   7  HPFS/NTFS
/dev/sda2            6375       38913   261369517+   f  W95 Ext'd (LBA)
/dev/sda5            6375       12748    51199123+   7  HPFS/NTFS
/dev/sda6           12749       19122    51199123+  83  Linux
/dev/sda7           19123       25496    51199123+   c  W95 FAT32 (LBA)
/dev/sda8           25497       31870    51199123+   7  HPFS/NTFS
/dev/sda9           31871       37949    48829536   83  Linux
/dev/sda10          37950       38913     7743298+  82  Linux swap / Solaris

```

---

### Post by geirha on 2008-10-07
My guess is /dev/sda1 wasn't unmounted cleanly from windows. Try mounting it manually from the terminal to see if it gives any error messages:
```
sudo mount /dev/sda1
```

If my guess was right, boot into windows, then shut it down/restart cleanly and boot back into ubuntu. Does it still not mount?

---

### Post by Julius1988 on 2008-10-07
yes windows was not properly shutdown, but i am not able to go into windows either is there a way to correct this problem from Linux.
> 
Why it only affects sda1 and not other drives?


---

### Post by vanadium on 2008-10-07
ntfsfix, from the ntfsprogs, can check and repair ntfs volumes.

---

### Post by Julius1988 on 2008-10-07
i got the following error
```

 sudo ntfsfix /dev/sda1
Mounting volume... Failed to startup volume: Invalid argument.
FAILED
Attempting to correct errors... FAILED
Failed to startup volume: Invalid argument.
Volume is corrupt. You should run chkdsk.

```
was there any error in my syntax?

---

### Post by vanadium on 2008-10-07
Your syntax is right. I have never used ntfsfix myself. I know it has basic repairing functionalities, but it is limited in what it can do. The manual states: > ntfsfix is NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS consistency check for the first boot into Windows.
The error message you get indicates to be that the damage is beyond what ntfsfix can repair. You will need to get Windows running and have the disk checked using the windows checking tools.

---

### Post by Julius1988 on 2008-10-07
k i will try to correct error from windows.

---

