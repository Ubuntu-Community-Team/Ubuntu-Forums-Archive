---
title: "(Harddrive?) Error Messages during boot process"
date: 2008-06-09
forum: Hardware
---

### Post by Ingrater on 2008-06-09
Since I upgraded to 8.04 from 7.10 lots of error occur during the booting process and it takes much longer than with 7.10. I asumed a failed upgrade and reinstalled 8.04 from scratch. It had no use.

Also all partitions of my 2 harddrives don't show up in ~/media/ after rebooting. I have to open them with the file browser (the file browser lists them correctly on the left) then they appear in ~/media/

Additionally I've got a USB-Harddrive connected to my computer. I already removed it and rebooted but the errors remained. Also I detached my two DVD-drives, but the errors also didn't vanish.

Those errors did not occur in 7.10 so I think it has to be an problem with something that has been added / updated since 7.10. Maybe a new driver.

The Errors
> [   84.477938] ata4.00: status: { DRDY }
[   84.477947] ata4: soft resetting link
[   84.823369] ata4.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[   84.823372] ata4.00: revalidation failed (errno=-5)
[   84.823373] ata4: failed to recover some devices, retrying in 5 secs
[   89.814901] ata4: soft resetting link
[   94.998227] ata4: port is slow to respond, please be patient (Status 0xd0)
[   99.803408] ata4: SRST failed (errno=-16)
[   99.803410] ata4: soft resetting link
[  104.987736] ata4: port is slow to respond, please be patient (Status 0xd0)
[  109.792917] ata4: SRST failed (errno=-16)
[  109.792921] ata4: soft resetting link
[  114.977244] ata4: port is slow to respond, please be patient (Status 0xd0)
[  120.117986] ata4.00: device is on DMA blacklist, disabling DMA
[  120.118332] ata4.00: configured for PIO4
[  120.118345] ata4: EH complete
[  150.050289] ata4.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[  150.050294] ata4.00: cmd c4/00:08:00:00:00/00:00:00:00:00/e0 tag 0 pio 4096 in
[  150.050295]          res 40/00:00:00:00:00/00:00:00:00:00/00 Emask 0x4 (timeout)
[  150.050297] ata4.00: status: { DRDY }
[  150.050305] ata4: soft resetting link
[  150.392623] ata4.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[  150.392625] ata4.00: revalidation failed (errno=-5)
[  150.392627] ata4: failed to recover some devices, retrying in 5 secs
[  155.382276] ata4: soft resetting link
[  155.727663] ata4.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[  155.727665] ata4.00: revalidation failed (errno=-5)
[  155.727667] ata4: failed to recover some devices, retrying in 5 secs
[  160.719258] ata4: soft resetting link
[  161.059728] ata4.00: failed to IDENTIFY (INIT_DEV_PARAMS failed, err_mask=0x80)
[  161.059731] ata4.00: revalidation failed (errno=-5)
[  161.059732] ata4.00: disabled
[  161.560372] ata4: EH complete

fdisk
> Platte /dev/sda: 300.0 GByte, 300069052416 Byte
16 Köpfe, 63 Sektoren/Spuren, 581421 Zylinder
Einheiten = Zylinder von 1008 × 512 = 516096 Bytes
Disk identifier: 0xad19911a

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               1       83220    41942848+   7  HPFS/NTFS
/dev/sda2           83221      290708   104573952    7  HPFS/NTFS
/dev/sda3   *      290710      581418   146517336    7  HPFS/NTFS

Platte /dev/sdb: 300.0 GByte, 300069052416 Byte
255 Köpfe, 63 Sektoren/Spuren, 36481 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0x5ff65ff6

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sdb2            2551        4838    18378360   83  Linux
/dev/sdb3            4839        5099     2096482+  82  Linux Swap / Solaris
/dev/sdb4            5100       36480   252067882+   f  W95 Erw. (LBA)
/dev/sdb5            5100       20790   126037926    7  HPFS/NTFS
/dev/sdb6           20791       36480   126029893+   7  HPFS/NTFS

Platte /dev/sdd: 1006 MByte, 1006108672 Byte
17 Köpfe, 32 Sektoren/Spuren, 3612 Zylinder
Einheiten = Zylinder von 544 × 512 = 278528 Bytes
Disk identifier: 0xc3072e18

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdd1               1        3613      982512    b  W95 FAT32 

/etc/fstab 
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=e002e21f-1202-450a-beed-0706bfca18bb /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=c6aaa863-06ad-4a5e-8422-efdf936652f0 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

Edit: forgett the part with the missing mount points, fixed that. Edited fstab manually. Still I'm wondering why those errors during booting occur.

---

### Post by skralljt on 2008-07-16
Though the following has not fixed my problem which is similar, it has helped many others:  buy an 80 pin ide cable.  You can tell they are 80 pins because there are twice as many wires, it probably says it in really small type on the cable, and the master/slave/mb ends are colorcoded black,grey,blue in that order.    good luck!`

---

### Post by a-guest-user on 2008-08-05
Did you find a solution for that? Because I'm having the same trouble with 8.04 and couldn't find a solution so far.

---

### Post by arch0njw on 2008-08-07
I get to change my reply here.  I was going a "me too", and then I found a solution.  The suggestion at this post worked for me very nicely:

[http://ubuntuforums.org/showthread.php?p=5540739](http://ubuntuforums.org/showthread.php?p=5540739)

---

### Post by Ocelaris on 2008-11-15
I ended up physically having a bad port on my motherboard, or cable, but I bypassed that port/cable (not sure, but it was one of them) and everything boots up nicely now... wheww...

---

### Post by smdofjmdsfjoiez on 2010-05-06
Ocelaris +1 
same issue here: physical bad port on my motherboard

---

