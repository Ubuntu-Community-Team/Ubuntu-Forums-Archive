---
title: "Ubuntu 8.04 Disk mounted but not visible within Places"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by buzz57 on 2009-01-21
I have added a new SATA Hard Disk and it appears to mount correctly according to the system
 fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x245a13ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4362    35037733+  83  Linux
/dev/sda2   *       15359       29784   115876845   83  Linux
/dev/sda3           29785       30401     4956052+   5  Extended
/dev/sda5           29785       30401     4956021   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a8993

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

when I issue a mount command it says it is already mounted and it is in fstab.
 fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x245a13ce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4362    35037733+  83  Linux
/dev/sda2   *       15359       29784   115876845   83  Linux
/dev/sda3           29785       30401     4956052+   5  Extended
/dev/sda5           29785       30401     4956021   82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000a8993

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux

But in places I cannot see the drive at all in "Places"

What have I done wrong? I have searched the forums to no avail any help appreciated.

---

### Post by taurus on 2009-01-21
Are you talking about the /dev/sdb1?  Can you post the outputs of these commands from a terminal?

```

sudo blkid
cat /etc/fstab
df -h
id
```

---

### Post by buzz57 on 2009-01-21
Thanks for the swift reply. Yes I am talking about /dev/sdb1. I am a newbie but I have searched and followed instructions but accept that I probably have made a mistake somewhere


cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=34b3060e-90a6-4910-affb-1c2bc44cf89f /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=d3310109-2d56-480c-84d7-b00a68bcd2fd none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/sdb1	/mnt/data	ext3	defaults	0	0
root@linux-desktop:/home/buzz# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             109G   99G  4.8G  96% /
varrun                882M  236K  881M   1% /var/run
varlock               882M     0  882M   0% /var/lock
udev                  882M   72K  882M   1% /dev
devshm                882M   12K  882M   1% /dev/shm
lrm                   882M   44M  838M   5% /lib/modules/2.6.24-23-generic/volatile
/dev/sdb1             232G  188M  220G   1% /sdb1
/dev/sdb1             232G  188M  220G   1% /mnt/data
root@linux-desktop:/home/buzz# id
uid=0(root) gid=0(root) groups=0(root)

---

### Post by taurus on 2009-01-21
You mount your /dev/sdb1 to /mnt/data so that's why you can't find it in Places.  Edit /etc/fstab and change the mount point from /mnt/data to /media/data.

```
/dev/sdb1 /media/data ext3 defaults 0 0
```
Save it.  Then, create a new mount point and reboot.

```
mkdir /media/data
```

p.s.  Just be real careful when you log in as root since that is what you are doing right now.

---

### Post by buzz57 on 2009-01-21
Thanks a million, that worked perfectly. Didn´t realise had to be in /media/ the docs hadn´t made it clear. On my other CentOS box i put the mount points in /mnt/ . I do not normally run as root except if I have a load of changes to make which I am confident with.

---

