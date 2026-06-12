---
title: "Cannot recognize DVD drive on new installation"
date: 2007-10-16
forum: Hardware &amp; Laptops
---

### Post by maxxum on 2007-10-16
Feisty would not install on my dell because it has a PATA DVDRW  (NEC ND-3500AG). So I made a boot USB stick, disabled the DVD drive in bios, and installed  KUbuntu. It works well except that after enabling the DVD drive in bios, it does not recognize it. There is no entry in fstab and I see some error in  the output of hwinfo. Let me post the fstab and fdisk. The hwinfo output on a file is too big to be attached.
fdisk -l:
```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7649    61440561    7  HPFS/NTFS
/dev/sda2            7650       15298    61440592+   7  HPFS/NTFS
/dev/sda3           18971       19457     3911827+  82  Linux swap / Solaris
/dev/sda4           15299       18970    29495340   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1           7       56196   de  Dell Utility
/dev/sdb2   *           8        4620    37053922+   7  HPFS/NTFS
/dev/sdb3            4621        9320    37752750    f  W95 Ext'd (LBA)
/dev/sdb4            9321        9725     3253162+  db  CP/M / CTOS / ...
/dev/sdb5            4621        4882     2104483+  82  Linux swap / Solaris
/dev/sdb6   *        4883        6156    10233373+  83  Linux
/dev/sdb7            6157        9320    25414798+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001   83  Linux

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       30401   244196001    f  W95 Ext'd (LBA)
/dev/sdd5            1472        2432     7719201   83  Linux
/dev/sdd6            2433       15169   102309921    b  W95 FAT32
/dev/sdd7           15170       30401   122351008+   b  W95 FAT32
/dev/sdd8               1        1471    11815713   83  Linux

Partition table entries are not in disk order

```

fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=0dd94763-a421-4e2c-b60d-0d29cd98628e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=46D4DC11D4DC0559 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=96F4D54EF4D5316B /media/sda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda3
UUID=19aa17ce-d189-4a9d-917e-fc53e4e3cd10 none            swap    sw              0       0
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto     0       0

```
Part of hwinfo:
```

>> block.1: block modules
----- exec: "/sbin/modprobe ide_cd " -----
  WARNING: Error inserting cdrom (/lib/modules/2.6.20-16-generic/kernel/drivers/cdrom/cdrom.ko): Operation not permitted
  FATAL: Error inserting ide_cd (/lib/modules/2.6.20-16-generic/kernel/drivers/ide/ide-cd.ko): Operation not permitted
----- return code: ? -----
----- exec: "/sbin/modprobe sr_mod " -----
  WARNING: Error inserting cdrom (/lib/modules/2.6.20-16-generic/kernel/drivers/cdrom/cdrom.ko): Operation not permitted
  FATAL: Error inserting sr_mod (/lib/modules/2.6.20-16-generic/kernel/drivers/scsi/sr_mod.ko): Operation not permitted
----- return code: ? -----
----- exec: "/sbin/modprobe st " -----
  FATAL: Error inserting st (/lib/modules/2.6.20-16-generic/kernel/drivers/scsi/st.ko): Operation not permitted
----- return code: ? -----
>> block.2: sysfs drivers
>> block.3: cdrom

```

---

### Post by maxxum on 2007-10-17
From the fstab, it seems that it has the partition of the USB stick (then it was sdb1) which I used to install Ubuntu being mounted on cdrom0. Of course when the USB stick was removed it found a hard drive partition by that name and is trying to mount it there. After my current reboot, there was no sdb at all. The four hard drives are sdc, sdd, sde and sdf respectively. 
I am hoping someone knows how to make it see the DVD drive, assign some drive id like sda and then I can edit the fstab to make it mount on cdrom0.
Else, I'll have to buy a SATA DVD RW! :)

---

### Post by maxxum on 2007-10-17
UPDATE: I put in a different DVD-ROM drive and it recognized and mounts it as soon as I put in a CD/DVD. I guess there is something with the NEC DVDRW (model ND-3500AG in case anyone is curious) drive then. I can use it in XP, but Vista cannot read DVDs from it (even though it sees it and says it is working properly) and Ubuntu does not see it at all. However this DVD-ROM (is a Sony) works in all three partitions.
I guess I'm gonna have to use XP when I need to burn a DVD. Will see what Gutsy does when I download it as it is up for release tomorrow.

---

