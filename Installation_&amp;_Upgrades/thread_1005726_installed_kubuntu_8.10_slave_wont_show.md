---
title: "installed kubuntu 8.10 slave wont show"
date: 2008-12-08
forum: Installation &amp; Upgrades
---

### Post by weirdfate on 2008-12-08
i installed kubuntu 8.10 and tried to get my slave drive formated but now it wont show up at all can some one point me in the correct direction to format my slave HD and get it to show up in linux so i can use it to store songs on please....  I have tried the tutorials [http://www.ehow.com/how_1000631_hard-drive-linux.html](http://www.ehow.com/how_1000631_hard-drive-linux.html) i found online but they were no help

drives dont sho up as HD they show up as SD

this is what i get when i try to show my drives 

weirdfate@weirdfate-desktop:~$ ls /dev/hd*
ls: cannot access /dev/hd*: No such file or directory
weirdfate@weirdfate-desktop:~$ ls /dev/sd*
/dev/sda   /dev/sda2  /dev/sdb   /dev/sdc
/dev/sda1  /dev/sda5  /dev/sdb1  /dev/sdc1

what one is my slave and how do i clean it out and mount it so i can use it

thank you

---

### Post by taurus on 2008-12-08
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by weirdfate on 2008-12-08
> **taurus said:**
> Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

weirdfate@weirdfate-desktop:~$ sudo fdisk -l
[sudo] password for weirdfate:

Disk /dev/sda: 60.0 GB, 60081831936 bytes
255 heads, 63 sectors/track, 7304 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcccdcccd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7000    56227468+  83  Linux
/dev/sda2            7001        7304     2441880    5  Extended
/dev/sda5            7001        7304     2441848+  82  Linux swap / Solaris

Disk /dev/sdb: 20.5 GB, 20525137920 bytes
255 heads, 63 sectors/track, 2495 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa79da79d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2495    20041056   86  NTFS volume set

Disk /dev/sdc: 1002 MB, 1002438656 bytes
65 heads, 32 sectors/track, 941 cylinders
Units = cylinders of 2080 * 512 = 1064960 bytes
Disk identifier: 0xbe72d4a6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         942      978928    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(956, 64, 32) logical=(941, 18, 32)


dont know if this helps but the drive i want to use for slave is 20g
yes i know i have small HD's

---

