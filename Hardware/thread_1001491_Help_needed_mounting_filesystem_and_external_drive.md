---
title: "Help needed mounting filesystem and external drive."
date: 2008-12-04
forum: Hardware
---

### Post by Jordan777 on 2008-12-04
Hey all.  I have a My Book WD 500GB hard drive but I can't seem to mount it while I'm using Xubuntu.  Also I want to mount my windows file system while I'm using Xubuntu.  I'm using one hard drive to dual boot XP and Xubuntu.  Can anyone tell me how to mount my external drive and XP file system?

---

### Post by gabril on 2008-12-04
I usually do this manually.

first look in the /dev directory and look up your sda drives... (im assuming you use satadrives?) The usbhdd will be there anyway.

Im assuming you have reformatted your WD to ntfs?

That is where the problem lies...

Try:

$mkdir /media/WD-500GB
$sudo mount -fs <the file system of your drive> /dev/sda<x> /media/WD-500GB

Not 100% sure about the -fs

check man mount on how to write this correctly... its under ntfs.. 

Hope this gave you the initial idea? then you can start modifying thunar to do this automatically! There ought to be a post in this forum on that...

---

### Post by taurus on 2008-12-04
Post the outputs of these commands from a terminal.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by Jordan777 on 2008-12-04
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001d285

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60801   488384001    b  W95 FAT32

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbec3bec3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       17847   143355996    7  HPFS/NTFS
/dev/sdb2           17848       20035    17575110   83  Linux
/dev/sdb3           20036       38913   151637535    5  Extended
/dev/sdb5           20036       20278     1951866   82  Linux swap / Solaris
/dev/sdb6           20279       38913   149685606   83  Linux

jordan@Bahamut:~$ sudo blkid
/dev/sda1: LABEL="My Book" UUID="B1D0-196E" TYPE="vfat" 
/dev/sdb1: UUID="221C2F311C2F0001" TYPE="ntfs" 
/dev/sdb2: UUID="03b4f91b-1685-405d-a2ec-29214b3c6977" TYPE="ext3" 
/dev/sdb5: TYPE="swap" UUID="8998cbff-623f-4f8c-af2d-72088e7c98a1" 
/dev/sdb6: UUID="80f0d3de-4b76-433c-9938-43e1999fcd60" SEC_TYPE="ext2" TYPE="ext3" 

jordan@Bahamut:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=03b4f91b-1685-405d-a2ec-29214b3c6977 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb6
UUID=80f0d3de-4b76-433c-9938-43e1999fcd60 /home           ext3    relatime        0       2
# /dev/sdb5
UUID=8998cbff-623f-4f8c-af2d-72088e7c98a1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
jordan@Bahamut:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb2              17G  2.3G   14G  15% /
tmpfs                1004M     0 1004M   0% /lib/init/rw
varrun               1004M  100K 1004M   1% /var/run
varlock              1004M     0 1004M   0% /var/lock
udev                 1004M  2.8M 1002M   1% /dev
tmpfs                1004M     0 1004M   0% /dev/shm
lrm                  1004M  2.4M 1002M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sdb6             141G  280M  134G   1% /home
jordan@Bahamut:~$ 


```

---

### Post by taurus on 2008-12-04
You can mount those two partitions, /dev/sda1 & /dev/sdb1, with

```
sudo mkdir /media/sda1 /media/sdb1
sudo mount -t vfat /dev/sda1 /media/sda1 -o umask=000
sudo mount -t ntfs-3g /dev/sdb1 /media/sdb1
df -h
```

---

### Post by Jordan777 on 2008-12-05
Thank you!!!!  Thanks you so much!  :D:KS

---

### Post by Jordan777 on 2008-12-09
Sorry to bother you guys again, but is there a way for me to get the drives to automatically be mounted every time I start up Kubuntu?

---

