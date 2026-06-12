---
title: "Help! Two of my disks are missing!"
date: 2007-10-29
forum: Hardware &amp; Laptops
---

### Post by Azyx on 2007-10-29
I hade a system with Dapper 6.06LTS, but I installed Gutsy (7.10), but keep my home partition. My problem is that Gutsy don't find 2 of my disk on this controller Card:
 (00:0d.0 RAID bus controller: Integrated Technology Express, Inc. IT/ITE8212 Dual channel ATA RAID controller (rev 13) )

The RAID-card are BIOS-configured as "IDE".

I have some problems to find the disks when i Installed the system under Dapper (Dapper called one hdx partition hdx2 instead of hdx1), But I saw them i gparted.

Now, only 2 of 4 disk are mounted, and if I open Gparted, I only see 2 disks, from the RAID-controller card. The 2 disks that are invisible are identical to one of the mounted disk (ATA ST3300831A) (279,46 GB) and have of Gutsy getting the namne /dev/sda1, but it is not any SCSI-device. This disk have also the Label = Set in GParted.

fstab look like this:
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=26cc6045-e56c-413d-829e-129c14b42a95 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda2
UUID=93ce9162-fb61-46d7-ac0c-58c29809cd84 /home           ext3    defaults        0       2
# /dev/sda1
UUID=feb51e21-b316-4f18-b1d1-d161c3a646f7 /media/sda1     reiserfs defaults        0       2
# /dev/sdb1
UUID=a1d838c2-5b99-495e-a97e-bb63392f1978 /media/sdb1     ext3    defaults        0       2
# /dev/hda3
UUID=68b59c58-33af-45de-9062-edc0ba3701f6 none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

I don't know that i should do to find my 2 missing ST3300831A disks on the RAID-bus controller. I also se that one of the diskt on the kontroller card have the name /dev/hda3 (mounting point /media/sdb1.

/Azyx

---

### Post by Azyx on 2007-10-30
I gonna install dapper agin, and next time i check with the live-cd if it works before i upgrade.

With dapper i can see all my disk.

---

### Post by deags on 2007-12-12
i have exact same problem!

---

