---
title: "Cannot access slave drive."
date: 2009-02-23
forum: Hardware
---

### Post by Indy452 on 2009-02-23
I have Xubuntu running nicely on a 1400 mhz P4 computer with a master ATA 20GB hd and a slave 30GB hd. Unfortunately the slave is seen by fdisk but I am unable to access it. Any tricks or tips I need to try to get it seen in my "home" folder?  I want to use the slave strictly as storage of digital music files.

If you can help me I would be very grateful.;)

---

### Post by taurus on 2009-02-23
What filesystem is your second harddrive, /dev/sdb1?  You need to add an entry to /etc/fstab to have it mount automatically each time you boot Xubuntu.

```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
id
```

---

### Post by Indy452 on 2009-02-23
neal@neal-desktop:~$ sudo fdisk -l
[sudo] password for neal: 

Disk /dev/sda: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92419241

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2327    18691596   83  Linux
/dev/sda2            2328        2434      859477+   5  Extended
/dev/sda5            2328        2434      859446   82  Linux swap / Solaris

Disk /dev/sdb: 30.0 GB, 30060527616 bytes
255 heads, 63 sectors/track, 3654 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000096

   Device Boot      Start         End      Blocks   Id  System
neal@neal-desktop:~$ 


I hate to have to post all this but this is what reads from fdisk.

I'm not even sure what the /dev/sda5 is?   So looking at this I see that sda1 has a small asterik next to it under boot. Should sda2 have an asterek also?  Does this mean sda2 is not loading at boot?  How do I alter it so it loads at boot? The command you gave me? (sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
id)

Thanks for the help.

---

### Post by Indy452 on 2009-02-24
Anyone know how I can boot the second drive (sda2) at startup?

Thanks.

---

### Post by taurus on 2009-02-24
You need to create a partition and format it (filesystem) on your second harddrive before you can use it.

```

Disk /dev/sdb: 30.0 GB, 30060527616 bytes
255 heads, 63 sectors/track, 3654 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000096

Device Boot Start End Blocks Id System

```
You can do it either from a terminal or install gparted which is a GUI.

```
sudo apt-get update
sudo apt-get install gparted
gksu gparted
```
The asterisk next to a partition means it's a bootable partition.  And your /dev/sda2 is an extended partition with swap parition, /dev/sda5, as a logical partition.

---

### Post by Indy452 on 2009-02-24
> **taurus said:**
> You need to create a partition and format it (filesystem) on your second harddrive before you can use it.

```

Disk /dev/sdb: 30.0 GB, 30060527616 bytes
255 heads, 63 sectors/track, 3654 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000096

Device Boot Start End Blocks Id System

```
You can do it either from a terminal or install gparted which is a GUI.

```
sudo apt-get update
sudo apt-get install gparted
gksu gparted
```
The asterisk next to a partition means it's a bootable partition.  And your /dev/sda2 is an extended partition with swap parition, /dev/sda5, as a logical partition.



Thanks taurus.  I think you have me on the right track. I appreciate this. I'm away from my computer now but I'll give it a whirl this eve.

Thanks again.

Neal:grin:

---

### Post by Indy452 on 2009-02-24
Actually, before I download gpated in xubuntu, can I use a live cd to format the drive?  If so which disk utility would you recommend?

Thanks again.

---

### Post by taurus on 2009-02-24
There is a gparted on the LiveCD so you can use that if you wish.  When you first open up gparted from the LiveCD, it should point at your first drive, /dev/sda, so use the drop down button on the right side to point to /dev/sdb.  Then create a partition and format it to ext3 since you only have Ubuntu on your machine so might as well use ext3 filesystem.

---

### Post by Indy452 on 2009-02-24
> **taurus said:**
> There is a gparted on the LiveCD so you can use that if you wish.  When you first open up gparted from the LiveCD, it should point at your first drive, /dev/sda, so use the drop down button on the right side to point to /dev/sdb.  Then create a partition and format it to ext3 since you only have Ubuntu on your machine so might as well use ext3 filesystem.

Sweet. Sounds easy enough.  I'll use the G-parted cd.  When creating the partition, I want to have as much space as possible as this is strictly for file storage. Will I have to specify a swap space then?  If so what amount? I currently have 768MG ram in the machine. Is swap supposed to be twice as much as you have ram?  (maybe I'm making this too complex for myself, I dunno.)

Thanks again.

---

### Post by taurus on 2009-02-24
You already have a swap partition on the first harddrive.

```
/dev/sda5 2328 2434 859446 82 Linux swap / Solaris
```
To see how much you have, run this command from a terminal and it will tell you.

```
free -m
```
Unless you want more swap space, I would use gparted and create one partition, /dev/sdb1, that takes up the whole disk space.  Then format it to ext3.  Save it and reboot into Xubuntu.  Now, edit /etc/fstab

```
gksu mousepad /etc/fstab
```
and add an entry at the end of that file for your new harddrive.

```
/dev/sdb1   /media/sdb1   ext3   defaults   0   2
```
Save it and exit the mousepad editing window.  Now, create the new mount point and mount it.

```
sudo mkdir /media/sdb1
sudo mount -a
df -h
```
And if you want to write to /media/sdb1 anytime you want without using sudo, you need to change the ownership of /media/sdb1 from root to your login name, assuming your login name is indy.

```
sudo chown -R indy:indy /media/sdb1
ls -la /media
```

---

### Post by Indy452 on 2009-02-24
Awesome!  Thank you, thank you, thank you!  Does this forum use the thanks anymore? I don't seem to see it. Oh well. Either way thanks:p

Neal

---

