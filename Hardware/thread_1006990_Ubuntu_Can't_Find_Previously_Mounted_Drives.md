---
title: "Ubuntu Can't Find Previously Mounted Drives"
date: 2008-12-09
forum: Hardware
---

### Post by Beavis6953 on 2008-12-09
Last week all of my drives were working fine. all mounted in my fstab Below. Now some of the the drives are not being recognized. All of the drives are being recognized in the BIOS. This is my fdisk -l:
##################################################################################################################################
dan@UBURock:~$ sudo fdisk -l

[sudo] password for dan: 



Disk /dev/sdb: 122.9 GB, 122942324736 bytes

255 heads, 63 sectors/track, 14946 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x9d649d64



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1               1       14946   120053713+   7  HPFS/NTFS



Disk /dev/sdc: 61.4 GB, 61492838400 bytes

255 heads, 63 sectors/track, 7476 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x23f523f4



   Device Boot      Start         End      Blocks   Id  System

/dev/sdc1               1        7476    60050938+   7  HPFS/NTFS



Disk /dev/sdd: 750.1 GB, 750156374016 bytes

255 heads, 63 sectors/track, 91201 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x0007922d



   Device Boot      Start         End      Blocks   Id  System

/dev/sdd1   *           1        6079    48829536   83  Linux

/dev/sdd2            6080        6225     1172745   82  Linux swap / Solaris

/dev/sdd3            6226       91201   682569720    7  HPFS/NTFS



Disk /dev/sde: 500.1 GB, 500107862016 bytes

255 heads, 63 sectors/track, 60801 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x69205244



   Device Boot      Start         End      Blocks   Id  System

/dev/sde1               1       60801   488384001    7  HPFS/NTFS

##################################################################################################################################

To be honest when rebooting for the 75th time I did see an error with the ntfs-3g and it did say fail in red on the right hand side. instead of saying ok.


/dev/sda1 /media/Music ntfs-3g    defaults    0 2

/dev/sdb1    /media/Software ntfs-3g defaults    0 2

/dev/sdc1    /media/Games ntfs-3g defaults    0 2

/dev/sdd1    /media/BackUp ntfs-3g defaults    0 2

/dev/sde3    /media/Shows ntfs-3g defaults    0 2

/dev/sdf1    /media/NewStuff ntfs-3g defaults    0 2


If anyone has any good ideas it would be awesome.

---

