---
title: "99% of issues solved -- please help with last one :)"
date: 2009-06-05
forum: Hardware
---

### Post by ron_jeremy on 2009-06-05
Searching this forum has helped me pretty much solve all my Jaunty issues & I am now ecstatic with this OS. My last hardware issue is as follows:

I have 3 optical drives installed:

[LIST]
[*]Pioneer DVD via PATA cable
[*]2 x Plextor PX-40TSi SCSI CDROM's
[/LIST]
The DVD drive was used to install Ubuntu & for pretty much most day to day stuff that involves optical media. This drive gives me NO issues.

I only use the Plextors to rip my audio collection to wav files. I have not used them since switching to Ubuntu because I was not ripping any audio discs (I had the cable unplugged at the adapter). Anyway, now I want to rip some more of my audio cd's but cannot do so. Both units can read **data** discs (retail & burned) just fine & give me icons on the desktop, but neither wants anything to do with music discs. I have tried both retail & burned audio discs & inserting these discs into either Plextor yields the following error:

[IMG]http://i72.photobucket.com/albums/i181/thanasi67/cdrom_error.png[/IMG]

I don't know if there's a Ubuntu "Device Manager" but I can "see" the drives in Nero if that helps anyone:

[IMG]http://i72.photobucket.com/albums/i181/thanasi67/cdroms2.png[/IMG]

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=301a4e12-5602-4421-9333-bfd80d968635 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=7cb0ee07-0bf7-403a-acd8-5baccc6f9085 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
ronjeremy@DOZER:~$ 


ronjeremy@DOZER:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x725ee134

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59483   477797166   83  Linux
/dev/sda2           59484       60801    10586835    5  Extended
/dev/sda5           59484       60801    10586803+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xae28e104

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488382464    7  HPFS/NTFS
ronjeremy@DOZER:~$

Any ideas for me to try?

---

### Post by markbuntu on 2009-06-06
You need the codecs for that. Just get the package

ubuntu-restricted-extras

---

### Post by ron_jeremy on 2009-06-10
I was going to install them but it looks like I already have the restricted packages...any other ideas?

---

### Post by cariboo on 2009-06-10
Try grip to rip your cd's, it is in the repositories.

---

### Post by ron_jeremy on 2009-06-10
Grip does not recognize that an audio disc is even in either Plextor, though it does work with my DVD drive (as was mentioned in my orig post).

---

### Post by ron_jeremy on 2009-06-21
Just giving this a bump -- could really use some help on this one :D

---

