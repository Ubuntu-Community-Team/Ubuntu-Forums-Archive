---
title: "Can't Delete(Read-only file system)"
date: 2005-12-01
forum: Hardware &amp; Laptops
---

### Post by groovywombat on 2005-12-01
well, I have another question, and i have been searching relentlessly for the answer, but i just can't find it, or it doesn't work.  my problem, is that i can't delete files or rename them on my external firewire hdd, it's fat32, and my fstab looks liek this
```
/dev/sda1	/media/LACIE	vfat    umask=000		0	0
```

when i type in 'ls -l /media'  i get

```
drwxrwxrwx  24 root root 32768 1969-12-31 19:00 LACIE
```

so maybe someone can help me becuase when i try to empty files from the recyle bin i'm told that the disk is a read only disk.  So i guess my question is, what am I missing? and how can i solve this
thanks
Gavin

---

### Post by aysiu on 2005-12-01
Are you sure your Lacie is /dev/sda1?

That /etc/fstab entry looks good, but apparently root is the owner of the Lacie drive.

What happens when you type in ```
df -h
sudo fdisk -l
```? Can you post the output here?

---

### Post by groovywombat on 2005-12-01
the output of df -h is 
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Ubuntu-root
                       41G   35G  4.1G  90% /
tmpfs                 507M     0  507M   0% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-9-386/volatile
/dev/hdb1             228M   19M  198M   9% /boot
/dev/hda2              49G   44G  5.7G  89% /media/barracuda
/dev/md0              147G  112G   28G  80% /media/raid0
/dev/sda1             233G  173G   61G  75% /media/LACIE

```

the out put of fdisk -l is

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Ubuntu-root
                       41G   35G  4.1G  90% /
tmpfs                 507M     0  507M   0% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-9-386/volatile
/dev/hdb1             228M   19M  198M   9% /boot
/dev/hda2              49G   44G  5.7G  89% /media/barracuda
/dev/md0              147G  112G   28G  80% /media/raid0
/dev/sda1             233G  173G   61G  75% /media/LACIE
gavin@Apollo:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/Ubuntu-root
                       41G   35G  4.1G  90% /
tmpfs                 507M     0  507M   0% /dev/shm
tmpfs                 507M   13M  494M   3% /lib/modules/2.6.12-9-386/volatile
/dev/hdb1             228M   19M  198M   9% /boot
/dev/hda2              49G   44G  5.7G  89% /media/barracuda
/dev/md0              147G  112G   28G  80% /media/raid0
/dev/sda1             233G  173G   61G  75% /media/LACIE
gavin@Apollo:~$ sudo fdisk -l
Password:

Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               2         906     7269412+   5  Extended
/dev/hda2   *         907        7297    51335676    c  W95 FAT32 (LBA)
/dev/hda5               2         906     7269381    7  HPFS/NTFS

Disk /dev/hdb: 46.1 GB, 46103371776 bytes
255 heads, 63 sectors/track, 5605 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1          31      248976   83  Linux
/dev/hdb2              32        5605    44773155    f  W95 Ext'd (LBA)
/dev/hdb5              32        5605    44773123+  8e  Linux LVM

Disk /dev/hde: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1               1        9732    78172258+  83  Linux

Disk /dev/hdf: 80.0 GB, 80054059008 bytes
255 heads, 63 sectors/track, 9732 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdf1               1        9732    78172258+  83  Linux

Disk /dev/md0: 160.0 GB, 160096583680 bytes
2 heads, 4 sectors/track, 39086080 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Disk /dev/md0 doesn't contain a valid partition table

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    c  W95 FAT32 (LBA)

```

anyway i'm pretty certain sda1 is the correct path
thanks

---

### Post by aysiu on 2005-12-01
Yeah, you're right. The only thing I can think of is maybe ```
sudo umount /media/LACIE
sudo mount -a
``` It may be possible, too, that the /media folder is some kind of special folder (that's the mount point my computer generates for my Lacie as well--/media/LACIE) and that if you created some bogus folder (not in /mnt or /media), like /home/LACIE and specified that in the /etc/fstab that it might mount with the parameters you specified.

---

### Post by groovywombat on 2005-12-01
ok well i'll try and mount it in /home  thansk for the help.  I'll do it right after a stimulating day at radioshack tomorrow

---

### Post by aysiu on 2005-12-01
[QUOTE=groovywombat]ok well i'll try and mount it in /home  thansk for the help.  I'll do it right after a stimulating day at radioshack tomorrow[/QUOTE] It's not a guarantee, but it's worth a shot...

---

