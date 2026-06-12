---
title: "can't mount my Harddrive"
date: 2007-10-30
forum: Hardware &amp; Laptops
---

### Post by amithaba on 2007-10-30
Hi, I'm pretty new to ubuntu and last time I noticed that my former harddisks 30 gb and 30
are now split up in 7 gb(file system) and 47 gb(not mounted).

The Problem is that the 47gb is not mounted. And I can't get it to mount. What mount options would you suggest I use?
The following options need to be specified 
Mount point
File system
Mount Option

What do you guys suggest I do?
thx

---

### Post by dabl on 2007-10-30
Open a console and enter ```
df -h
``` and post the output.

Also do ```
blkid
``` and post that.

You'll need the ID of the partition, and the filesystem type, and then you'll use that information to put a mount line in your /etc/fstab file.   Probably if you search this forum on "fstab" you'll find many examples.

:)

---

### Post by amithaba on 2007-10-30
temuchin@sch321:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             7.0G  6.5G   97M  99% /
varrun                252M   92K  252M   1% /var/run
varlock               252M     0  252M   0% /var/lock
procbususb            252M  136K  252M   1% /proc/bus/usb
udev                  252M  136K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   33M  219M  14% /lib/modules/2.6.20-16-generic/volatile
/dev/scd0             604M  604M     0 100% /media/cdrom0


temuchin@sch321:~$ blkid
/dev/sda1: UUID="773f97a7-e861-4fdf-8b3b-7b2616890668" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="d4dd42f0-8b9a-4031-a811-2666260bd79c" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="ddc058c8-d8ee-4b9a-8f8f-0de3631ab80b" TYPE="swap" 
/dev/sda6: UUID="5d9be31e-c6d0-4c46-8b26-66b6e63d562c" TYPE="swap" 

File system is ext3
that's all I can find out :(

many thanx allready

---

