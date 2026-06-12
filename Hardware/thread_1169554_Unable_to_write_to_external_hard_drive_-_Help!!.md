---
title: "Unable to write to external hard drive - Help!!"
date: 2009-05-25
forum: Hardware
---

### Post by smirnoff76 on 2009-05-25
Hi All, 

I have a Western Digital external hard drive which I have had for a while now and previously have been able to write to it no problem. 

I recently did a re-install of 8.04 and since then have not been able to write to the hard drive. 

This morning I have backed up my files and have formatted the file system to resierfs (shows up in gparted as /dev/sdf). 

Even since doing that I am still unable to write to the hard drive, create folders etc, can anyone help??

Thanks

---

### Post by taurus on 2009-05-25
Can you just change the ownership of that mount point for that drive from root to your login name?

```
sudo chown -R username:username /mount_point
```

---

### Post by smirnoff76 on 2009-05-25
Just tried that now and get:

chown: cannot access `/mount_point': No such file or directory

---

### Post by taurus on 2009-05-25
You need to put in the _actual_ mount point for that external drive!  /mount_point is just an example that I used.

---

### Post by smirnoff76 on 2009-05-25
Doh!

Okay ran the command sudo chown -R smirnoff:smirnoff /dev/sdf and didn't give me any sort of return.
Unmounted the drive disconnected and then re-connected and still wont let me write to it?

---

### Post by taurus on 2009-05-25
/dev/sdf is not your mount point; it's your raw device!  A mount point would look something like /media/windows (or whatever you call it).  Why don't you just post the outputs of these commands from a terminal then?

```
sudo fdisk -l
df -h
```

---

### Post by smirnoff76 on 2009-05-25
Thanks for this Taurus! Output is as follows:

smirnoff@Area-51:~$ sudo fdisk -l

Disk /dev/sda: 750.1 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c879c87

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       90447   726515496   83  Linux
/dev/sda2           90448       91201     6056505    5  Extended
/dev/sda5           90448       91201     6056473+  82  Linux swap / Solaris

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60801   488384001   83  Linux
smirnoff@Area-51:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             688G  176G  477G  27% /
varrun               1010M  116K 1010M   1% /var/run
varlock              1010M     0 1010M   0% /var/lock
udev                 1010M   68K 1010M   1% /dev
devshm               1010M   12K 1010M   1% /dev/shm
lrm                  1010M   40M  971M   4% /lib/modules/2.6.24-24-generic/volatile
gvfs-fuse-daemon      688G  176G  477G  27% /home/smirnoff/.gvfs
/dev/sdf1             466G   33M  466G   1% /media/disk
smirnoff@Area-51:~$

---

### Post by taurus on 2009-05-25
```
sudo chown -R smirnoff:smirnoff /media/disk
ls -la /media
```

---

### Post by smirnoff76 on 2009-05-25
Just ran the first command and got the error:

chmod: invalid mode: `smirnoff:smirnoff'

---

### Post by 00czar00 on 2010-04-19
I had kind of the same problem and i did all that it said to do, and my hard drive still does not let me write or manage the disk....when i right click then go to properties it still say root is the owner (under "PERMISSION") but when i run " ls -la /media" it shows me as the owner.   ????????????????????????????:confused::confused::confused::confused::confused::confused::confused::confused:

---

### Post by 00czar00 on 2010-04-21
nvm it worked fine once i rebooted! thanks!

---

### Post by Raizen44 on 2010-09-04
> **taurus said:**
> ```
sudo chown -R smirnoff:smirnoff /media/disk
ls -la /media
```


Having a few problems too.... same prob with an external HDD. 100GB is usable, formatted for Linux while 150GB is formatted for windows. here are the results for the commands. any help would be great, guys...:

urian@urian-laptop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b4cf1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37419008   83  Linux
/dev/sda2            4659        4864     1648641    5  Extended
/dev/sda5            4659        4864     1648640   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8e3865c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18238   146489190    6  FAT16
/dev/sdb2           18238       30402    97709057    5  Extended
/dev/sdb5           18239       30401    97699297+  83  Linux
urian@urian-laptop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b4cf1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4659    37419008   83  Linux
/dev/sda2            4659        4864     1648641    5  Extended
/dev/sda5            4659        4864     1648640   82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8e3865c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18238   146489190    6  FAT16
/dev/sdb2           18238       30402    97709057    5  Extended
/dev/sdb5           18239       30401    97699297+  83  Linux

help please?

BTW:, I tried the other command as "/media/FREECOM HDD", not working. help would be appreciated.

urian@urian-laptop:~$ sudo chown -R urian:urian /media/FREECOM HDD
chown: cannot access `/media/FREECOM': No such file or directory

---

### Post by Lateralis on 2010-09-04
I haven't read all of your post, save for the last line. 

You need to escape spaces in commands.  To the shell "/media/FREECOM HDD" looks like /media/FREECOM with a command line argument of HDD.  You need to go "media/FREECOM\ HDD".

---

