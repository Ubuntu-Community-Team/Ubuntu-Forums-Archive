---
title: "Cannot mount drive"
date: 2008-11-17
forum: General Help
---

### Post by mab1376 on 2008-11-17
this used to work fine now all of a sudden it stopped. it says:

```
mount_point cannot contain the following characters: newline, G_DIR_SEPERATOR (usually /)
```

i'm running 8.10 100% up to date.

---

### Post by taurus on 2008-11-17
Are you trying to mount that drive from /etc/fstab?  Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by mab1376 on 2008-11-17
I'm trying to mount sdc1 should be labeled as External.

```

sudo fdisk -l
[sudo] password for mark: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03a903a9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38776   311464784    7  HPFS/NTFS

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4d6ad8de

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1           22868       30162    58597087+  83  Linux
/dev/sdb2   *           2       22867   183671145    f  W95 Ext'd (LBA)
/dev/sdb3           30163       30515     2835472+  82  Linux swap / Solaris
/dev/sdb5               2       22867   183663672    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000db6dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS
mark@mark-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=e9c70ec9-1b01-4699-8102-bf30ed702a45 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb3
UUID=545f75a3-865e-4a12-bdd3-01d180921325 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
mark@mark-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              56G  4.6G   48G   9% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  324K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1009M   1% /dev
tmpfs                1012M  184K 1012M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-7-generic/volatile

```

---

### Post by mab1376 on 2008-11-18
any ideas?

---

### Post by vanadium on 2008-11-18
You have probably been trying to change the mount point using the graphical interface (right-clicking the drive, properties). I guess you have entered a path in there (e.g. /media/External). This is invalid, but the gui won't tell you. This is a useability error that still has not been fixed. Resolution: go back into the drive properties and delete the entry you made there.

You could just enter "external", but the best way to have a drive mounted with the name of your choice is to label the volume. See [https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive) for how to do that (unfortunately, Linux does not have a unified easy graphical interface to apply volume labels: you need the command line).

Advantage: the drive will be mounted with the name of your choice on any computer because the label stored on the disk is being used as the name.

---

### Post by mab1376 on 2008-11-18
Thanks i'll try that later.

---

### Post by mab1376 on 2008-11-18
my device is not in my fstab, but it shows up in the fdisk -l

what should i do?

---

### Post by vanadium on 2008-11-19
?? Did you read my post?

---

### Post by mab1376 on 2008-11-25
Fixed it:


```
sudo mkdir /media/NTFS_USB
mount -t ntfs-3g /dev/sdc1 /media/NTFS_USB -o force
```

---

