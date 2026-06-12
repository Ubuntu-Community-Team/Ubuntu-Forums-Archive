---
title: "hard drive problems. (read only, missing partition)"
date: 2007-10-12
forum: Hardware &amp; Laptops
---

### Post by muuwt1 on 2007-10-12
i have a number of issues. if you can help with any, please advise.

i have one internal 80 gig hard drive. when i was using windows i partitioned it. one drive has all my system files for windows. and the other is just storage for internet downloads and music. so when i view my files in windows. where are my linux files? ive downloaded a few things in linux and saved them in my home folder. when i look for the files i cant seem to find them. 

so my read only problem. when i open the places menu. there is only one harddrive. hdd1. and its the partition with my windows system files and a few other important things. i can copy from it but i cant write files to it. 
ive tried a few commands

```
Muuwt@Muuwt:~$ sudo chown Muuwt /media/hda1
Password:
chown: changing ownership of `/media/hda1': Read-only file system
Muuwt@Muuwt:~$ sudo nautilus

(nautilus:8610): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.
Muuwt@Muuwt:~$ su
Password: 
root@Muuwt:/home/Muuwt# nautilus

(nautilus:8658): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(nautilus:8658): libgnomevfs-WARNING **: Failed to open session DBUS connection: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Volume monitoring will not work.

```

yea maybe changing to root didnt do anything. but just trying to figure stuff out...

my final problem is that my other partition is missing. i havent really tried to fix it yet, but just taking it one step at a time. you know?

thanks for anything
-muuwt

---

### Post by logos34 on 2007-10-12
In a terminal run 
[B]
sudo fdisk -l[/B]

and post it.

Windows doesn't recognize linux partitions.  If you want to read/access ubuntu from windows get [fs-driver]("http://www.fs-driver.org/").

Linux can't write to ntfs natively--you need the ntfs-3g driver.
[B]
sudo apt-get install ntfs-config[/B]

Then enable support:

**sudo ntfs-config**

> x enable write support internal drive

---

### Post by muuwt1 on 2007-10-13
```

muuwt@Muuwt:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        7649    40957717+   7  HPFS/NTFS
/dev/hda3            7650        7777     1028160   82  Linux swap / Solaris
/dev/hda4            7778        9729    15679440   83  Linux

muuwt@Muuwt:~$ sudo apt-get install ntfs-config
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfs-config

muuwt@Muuwt:~$ sudo ntfs-config
sudo: ntfs-config: command not found

```

accessing linux from windows isnt really something that needs to be fixed i was just curious.
so i have no idea why the commands failed. hopefully you do?

---

### Post by logos34 on 2007-10-13
> **muuwt1 said:**
> accessing linux from windows isnt really something that needs to be fixed i was just curious. so i have no idea why the commands failed. hopefully you do?

If you're on 7.04 Feisty:

Open up Synaptic package manager>Settings>repositiories>Ubuntu software tab>check **universe**

then try the commands again.

Otherwise see:
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

---

### Post by muuwt1 on 2007-10-13
thanks so much. it all works perfectly and now i can see both my partitions and they are both writable. 
-muuwt

---

