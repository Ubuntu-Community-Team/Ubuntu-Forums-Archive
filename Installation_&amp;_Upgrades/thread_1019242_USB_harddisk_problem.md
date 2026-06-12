---
title: "USB harddisk problem"
date: 2008-12-22
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-12-22
I got troubles with a new USB hard disk. Maybe it is just the Xmas rush and I am not thinking clear.

I plug in the harddisk (250G, Win95,LBA) just from the store and it will not be automounted!

I use:
sudo mount /dev/sdd1 /mnt/sdd1 -o user,rw

mounted!

I want to create a directory: Permission denied, so I try sudo mkdir abc

created!

I want to change the owner to a user of that directory: Permission denied (even with sudo)

I want to dd a partition (8GB) to this new hard disk, at 4GB the dd stops with the message: File too large.

What am I doing wrong? NO, don't tell me what I am doing wrong, tell me how to do it right ;-)

bye

Ronald

---

### Post by logos34 on 2008-12-23
fat32 doesn't understand the permissions linux does.  Max file size: 4 GB.

Reformat as NTFS or better yet ext3:

[https://help.ubuntu.com/community/InstallingANewHardDrive#Partition%20The%20Disk](https://help.ubuntu.com/community/InstallingANewHardDrive#Partition%20The%20Disk)
[https://help.ubuntu.com/community/Mount/USB#Automounting](https://help.ubuntu.com/community/Mount/USB#Automounting)

Edit ownership and permissions (chown and chmod):
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
(->bottom)

---

### Post by aitjcize on 2008-12-23
> **ELMIT said:**
> 

I want to change the owner to a user of that directory: Permission denied (even with sudo)


Ronald

sudo mount /dev/sdd1 /mnt/sdd1 -o user,rw**,uid=1000,gid=046**

but it's strange that it didn't automount...

---

### Post by vanadium on 2008-12-23
An USB drive should automount. There is some problem if it does not. The file system might need to be checked. If it is an ntfs formatted drive, check it using MS Windows. If you do not have MS Windows, then reformat the drive to a native linux file system (typically you would use ext3).

---

### Post by ELMIT on 2008-12-24
I have reformated the drive to a NTFS drive, because I need this USB hard disk also for Windows. Change permission was then allowed again.

automount does not work and I have no idea why.
I have already several threads about that here. A USB flash drive with 128MB is automounted, but a 8GB not. The USB harddisk is not automounted.

I hope we can find that one too. I do not know where settings are for automount. I have a desktop and a notebook, both Ubuntu and both have the same automount problem!

bye

R.

---

