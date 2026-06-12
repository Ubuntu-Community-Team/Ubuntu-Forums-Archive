---
title: "Trouble auto mount NTFS partitions"
date: 2005-05-07
forum: Hardware &amp; Laptops
---

### Post by fallsroad on 2005-05-07
I followed the guide to have my three NTFS partitions auto mount on boot up, and have had success with all but one, a SATA drive. I can get it to mount, but when I reboot, it does not auto mount while the rest will.

Here is the partition list:

------------------

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6432    51665008+   7  HPFS/NTFS
/dev/hda2            7709       14457    54211342+  83  Linux
/dev/hda3            6433        7708    10249470   83  Linux
/dev/hda4           14458       14593     1092420   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       24321   195358401    7  HPFS/NTFS

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       14593   117218241    7  HPFS/NTFS

----------------------------------------

And this is the relevant part of the /etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /home           ext3    defaults        0       2
/dev/hda4       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    umask=0222      0       0
/dev/sda1       /media/windowse ntfs    umask=0222      0       0
/dev/hdc1       /media/windowsf ntfs    umask=0222      0       0

-------------------------------

I altered the mount directories to reflect the drive lietters under Windows - make it easier to recall which drive is which. I'd like to get it so the SATA drive also mounts at boot.

Any help is much appreciated.

---

### Post by fallsroad on 2005-05-07
*bump*

Anyone?

---

### Post by dcockayne on 2005-05-10
Sorry, not a solution but I'm also interested in how to do this but have been unable to find a guide, could you post the URL and I'll let you know how I get on afterwards.

I'm a linux newbie and I've just switched over from trying suse (which automounts everything for you), kubuntu is great! :)

---

### Post by fallsroad on 2005-05-10
Automount NTFS: [http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

Automount FAT: [http://ubuntuguide.org/#automountfat](http://ubuntuguide.org/#automountfat)

Works fine for EIDE drives, and probably for some SATA drives, just not mine. :)

---

### Post by poofyhairguy on 2005-05-12
What SATA card do you have? Some aren't supported. Some need work. See if this helps, its the best I can do:

[http://www.ubuntuforums.org/showthread.php?t=30233&highlight=ntfs](http://www.ubuntuforums.org/showthread.php?t=30233&highlight=ntfs)

---

### Post by fallsroad on 2005-05-12
[QUOTE=poofyhairguy]What SATA card do you have? Some aren't supported. Some need work. See if this helps, its the best I can do:

[/QUOTE]

I'll give that a try. My ASUS A7V8X came with quasi-native support for SATA via a Promise controller on the mobo. Unfortunately, to get it to work with XP even as a secondary drive, I had to run a RAID 0 array, but with only a single drive. Weird, I know, but it is apparently the only way to get this to work.

However, Ubuntu recognizes the drive as sda and can read it'sa contents once it is manually mounted, so your fix might work for me. I'll give a try soon as I have time, and post back.

---

