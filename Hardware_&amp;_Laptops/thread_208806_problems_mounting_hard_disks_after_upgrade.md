---
title: "problems mounting hard disks after upgrade"
date: 2006-07-04
forum: Hardware &amp; Laptops
---

### Post by el_ricardo on 2006-07-04
hi, i just recently upgraded to ubuntu 6.06, and neither of my hard drives will now mount, when i try to browse them, i get a message saying:

error: device /dev/hdb1 is not removable

error: could not execute pmount

and the same goes for /dev/hdb2

any helpo would be great, cheers!

---

### Post by aysiu on 2006-07-04
Can you post the output of these three commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by el_ricardo on 2006-07-04
heres what it gave me:

```
~$sudo fdisk -l

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        5737    46082421    7  HPFS/NTFS
/dev/hdb2            5738        9729    32065740    b  W95 FAT32

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30024   241167748+  83  Linux
/dev/sda2           30025       30401     3028252+   5  Extended
/dev/sda5           30025       30401     3028221   82  Linux swap / Solaris

Disk /dev/sdd: 255 MB, 255852544 bytes
16 heads, 32 sectors/track, 976 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         976      249805+   6  FAT16

~$df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             227G  5.1G  210G   3% /
varrun                506M   80K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  172K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-25-386/volatile
/dev/sdd1             244M  168M   76M  69% /media/LEXAR MEDIA
/dev/hdb1              44G   42G  2.8G  94% /tmp/disks-conf-hdb1

~$cat /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

---

### Post by aysiu on 2006-07-04
Try this: ```
sudo umount /dev/hdb1
sudo mkdir */windows1*
sudo mkdir */windows2*
sudo cp /etc/fstab /etc/fstab_backup
gksudo gedit /etc/fstab
``` Add these two lines in at the end: ```
/dev/hdb1 */windows1* ntfs nls=utf8,umask=0222 0 0
/dev/hdb2 */windows2* vfat iocharset=utf8,umask=000 0 0
``` Save and exit Gedit. ```
sudo mount -a
``` You can change */windows1* and */windows2* to something else if you want, but otherwise, it's a good idea to copy and paste these commands instead of retyping them--faster, less room for error.

---

### Post by el_ricardo on 2006-07-04
thanks, that got it working for me, the command "gksudo gedit /etc/fstab" however wouldn't work, when i typed i got this:

```
(gedit:7771): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

and then it just hung and i had to restart the terminal, so i opened fstab in root by browsing to it and it worked, now i'm worried about that error message .... atleast i can access my hard disk now though, thanks!

---

