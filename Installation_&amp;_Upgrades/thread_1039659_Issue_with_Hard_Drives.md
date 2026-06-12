---
title: "Issue with Hard Drives"
date: 2009-01-14
forum: Installation &amp; Upgrades
---

### Post by codfishy on 2009-01-14
Okay.  I successfully installed Ubuntu for the very first time about 3 hours ago.

I installed 8.04, and I will upgrade to 8.10 when I have the chance to.

There is one MAJOR problem though:  Ubuntu cannot use the SATA (500GB) drive I just bought.  It reads it, as it shows it as "SCSI Drive".
I also have another problem, where Ubuntu can read the drive Windows XP is on.  It says "unable to mount location" and under it says "can't mount file".

So these are my questions:

1. How can I get my Ubuntu(and Windows XP) to read the 500 GB Drive so that I can use both OS's to see the same things I save in the Drive?  Will I need to create a partition in Windows?

2. Can I get Ubuntu to not display the Drive my XP is on?  I just don't want to see the drive since I'm not gonig to be using it.

Thanks.

---

### Post by taurus on 2009-01-14
Before you can use the new drive, 500GB, you first need to create a partition (probably /dev/sdb1) and format it, creating a filesystem.

What are the outputs of these commands from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by codfishy on 2009-01-14
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x71f88b33

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x57a97cd1

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       16709   134215011    7  HPFS/NTFS
/dev/hda2           16710       19457    22073310   83  Linux


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=1ac415fd-428b-4c67-aa69-dc68c54bdb9a /               ext2    errors=remount-ro 0       1
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2              21G  2.1G   18G  11% /
varrun               1014M  100K 1014M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
udev                 1014M   48K 1014M   1% /dev
devshm               1014M  136K 1014M   1% /dev/shm
lrm                  1014M   38M  976M   4% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       21G  2.1G   18G  11% /home/username/.gvfs
/dev/hda1             128G  107G   22G  84% /media/disk

---

