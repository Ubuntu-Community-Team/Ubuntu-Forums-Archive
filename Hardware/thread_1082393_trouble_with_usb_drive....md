---
title: "trouble with usb drive..."
date: 2009-02-27
forum: Hardware
---

### Post by zander1013 on 2009-02-27
hi,

i am using gparted to format a 1tb external drive using gparted. when i get done i cannot write to the disk. i have looked around gparted for a way to change ownership r/w permissions etc but i cant seem to get anywhere.

i have tried to smaller partitions but it did not seem to make a difference.


please advise.

zander

---

### Post by taurus on 2009-02-27
What filesystem did you format your 1TB external drive to?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by zander1013 on 2009-02-27
> **taurus said:**
> What filesystem did you format your 1TB external drive to?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

hi,

here is the output...

af@node0:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00034e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000207286272 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00095d71

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       57367   460800396   83  Linux
/dev/sdb2           57368      114734   460800427+  83  Linux
/dev/sdb3          114735      121601    55159177+  83  Linux
af@node0:~$ 

... thank you for helping...
and it was format to ext3 if it is not shown here. (i think) i have made several attempts with different file system formats.

zander

---

### Post by taurus on 2009-02-27
So you divided your 1TB external drive into three primary partitios:  /dev/sdb1, /dev/sdb2, & /dev/sdb3.  Have you mounted all three of them?

```
df -h
```
_Assuming_ you have mounted them all (/dev/sdb1 to /media/sdb1, /dev/sdb2 to /media/sdb2, and /dev/sdb3 to /media/sdb3), you can change the ownership of these three mount points from root to your login name, af, so you can write to them anytime you want.

```
sudo chown -R af:af /media/sdb1
sudo chown -R af:af /media/sdb2
sudo chown -R af:af /media/sdb3
ls -la /media
```

---

### Post by zander1013 on 2009-02-27
> **taurus said:**
> So you divided your 1TB external drive into three primary partitios:  /dev/sdb1, /dev/sdb2, & /dev/sdb3.  Have you mounted all three of them?

```
df -h
```
_Assuming_ you have mounted them all (/dev/sdb1 to /media/sdb1, /dev/sdb2 to /media/sdb2, and /dev/sdb3 to /media/sdb3), you can change the ownership of these three mount points from root to your login name, af, so you can write to them anytime you want.

```
sudo chown -R af:af /media/sdb1
sudo chown -R af:af /media/sdb2
sudo chown -R af:af /media/sdb3
ls -la /media
```


yes they are mounted but the "Create Folder" option is grayed out when i left click over the partition browser. here is what happed when i tried the commands you gave...

af@node0:~$ sudo chown -R af:af /media/sdb1
[sudo] password for af: 
chown: cannot access `/media/sdb1': No such file or directory
af@node0:~$ 


changing the tail of the command to partition lable names seems to be working though.

(i am using ubuntu 8.10)

also, can i change them so that all users can read and write to them?

thank you,

zander

---

### Post by zander1013 on 2009-02-27
here is the output from chown and ls with the partition labels replacing the drive mounts...

af@node0:/media$ sudo chown -R af:af /media/Hercules1
[sudo] password for af: 
af@node0:/media$ sudo chown -R af:af /media/Hercules2
af@node0:/media$ sudo chown -R af:af /media/Scratch
af@node0:/media$ ls -la /media
total 28
drwxr-xr-x  6 root root 4096 2009-02-27 15:05 .
drwxr-xr-x 20 root root 4096 2009-01-30 22:10 ..
lrwxrwxrwx  1 root root    6 2009-01-30 16:51 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2009-01-30 16:51 cdrom0
-rw-r--r--  1 root root  190 2009-02-27 15:05 .hal-mtab
-rw-------  1 root root    0 2009-02-27 15:04 .hal-mtab-lock
drwxr-xr-x  3 af   af   4096 2009-02-09 23:02 Hercules1
drwxr-xr-x  3 af   af   4096 2009-02-09 23:09 Hercules2
drwxr-xr-x  3 af   af   4096 2009-02-09 23:10 Scratch
af@node0:/media$ 

but even after unmounting and remounting the "Create Folder" option is still grayed out in file browsers that open when you click on the desktop icons for the partitions. :mad:

---

### Post by zander1013 on 2009-02-28
this did solve the problem after reboot.

thank you.

---

