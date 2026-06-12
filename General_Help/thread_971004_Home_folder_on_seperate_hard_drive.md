---
title: "Home folder on seperate hard drive"
date: 2008-11-04
forum: General Help
---

### Post by SeanArronD on 2008-11-04
I have just moved my home folder onto a separate hard drive using this tutorial: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

However, when i look at the disk to which Ubuntu is installed in gparted, it says that 84Gb is used when this should be significantly less now that i have moved the home folder onto another hard drive.

Anybody know why this has happened and also a way to fix this?

Thanks

---

### Post by taurus on 2008-11-04
Did you actually "move" or did you just "copy" them over?  What are the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by SeanArronD on 2008-11-04
sudo fdisk -l gives me:

> Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7cdb0844

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         653     5245191   82  Linux swap / Solaris
/dev/sda2   *         654       19457   151043130   83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00096b06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001   83  Linux


cat /etc/fstab gives me:

> # <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda1
UUID=4dbf4e08-7845-44a3-8266-ee2f0298dcf7      none            swap        sw          0   0
# /dev/sda2
/dev/sda2     /               ext3        defaults,errors=remount-ro    0   1

/dev/sdb1	/home		ext3	nodev,nosuid	0	2


df -h gives me:

> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2             143G   84G   53G  62% /
varrun                506M  256K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   68K  506M   1% /dev
devshm                506M   92K  506M   1% /dev/shm
/dev/sdb1             230G   70G  149G  32% /home
gvfs-fuse-daemon      143G   84G   53G  62% /home/seanarrond/.gvfs
/dev/scd0             2.5G  2.5G     0 100% /media/UDF Volume


---

### Post by ugm6hr on 2008-11-04
Did you delete the backup (after reboot):
```
sudo rm -rf /home_backup
```

---

### Post by SeanArronD on 2008-11-04
yea, have removed the home backup.

---

### Post by taurus on 2008-11-04
What's the output of this command from a terminal then?

```
ls -la /
```

---

### Post by SeanArronD on 2008-11-05
ls -la / gives me:

> total 112
drwxr-xr-x  24 root root        4096 2008-11-05 01:48 .
drwxr-xr-x  24 root root        4096 2008-11-05 01:48 ..
drwxr-xr-x   2 root root        4096 2008-10-23 09:03 bin
drwxr-xr-x   3 root root        4096 2008-10-28 09:03 boot
lrwxrwxrwx   1 root root          11 2008-06-17 16:52 cdrom -> media/cdrom
drwxr-xr-x  13 root root       14380 2008-11-04 22:33 dev
drwxr-xr-x 153 root root       12288 2008-11-05 14:17 etc
drwxrwxr-x   5 root seanarrond  4096 2008-11-04 20:56 home
drwxrwxrwx   2 root root        4096 2008-08-12 04:40 host
drwxr-xr-x   2 root root        4096 2008-04-22 18:48 initrd
lrwxrwxrwx   1 root root          33 2008-10-15 09:42 initrd.img -> boot/initrd.img-2.6.24-21-generic
lrwxrwxrwx   1 root root          33 2008-06-17 16:22 initrd.img.old -> boot/initrd.img-2.6.24-19-generic
drwxr-xr-x  16 root root       12288 2008-10-23 09:03 lib
drwx------   2 root root       16384 2008-06-17 16:52 lost+found
-r--r--r--   1 root root           0 2008-08-11 13:49 .m6rE
drwxr-xr-x  10 root root        4096 2008-11-04 21:04 media
drwxr-xr-x   2 root root        4096 2008-04-15 06:53 mnt
drwxr-xr-x   5 root root        4096 2008-08-11 23:45 opt
dr-xr-xr-x 177 root root           0 2008-11-04 21:03 proc
drwxr-xr-x   2 root root        4096 2008-10-30 18:46 $RECYCLE.BIN
drwxr-xr-x  22 root root        4096 2008-11-05 01:48 root
drwxr-xr-x   2 root root        4096 2008-10-15 09:41 sbin
drwxr-xr-x   2 root root        4096 2008-04-22 18:48 srv
drwxr-xr-x  12 root root           0 2008-11-04 21:03 sys
drwxrwxrwt  20 root root        4096 2008-11-05 18:12 tmp
drwx------   4 root root        4096 2008-11-04 20:36 .Trash-0
drwxr-xr-x  14 root root        4096 2008-09-07 01:12 usr
drwxr-xr-x  17 root root        4096 2008-09-07 01:11 var
lrwxrwxrwx   1 root root          30 2008-10-15 09:42 vmlinuz -> boot/vmlinuz-2.6.24-21-generic
lrwxrwxrwx   1 root root          30 2008-06-17 16:22 vmlinuz.old -> boot/vmlinuz-2.6.24-19-generic


---

### Post by CatKiller on 2008-11-05
**baobab** (or Disk Usage Analyzer if you launch it from the menu) will show you the amount of space that's taken up by different folders, in case the usage is from somewhere other than /home.

Note that the filesystem tree it uses is the complete filesystem tree, so it will show the useage of /home as well, without showing files on different partitions differently.

---

### Post by SeanArronD on 2008-11-05
the problem no longer matters. i have just formatted the hard drive and am going to reinstall ubuntu so all is good.

thanks for the help.

---

