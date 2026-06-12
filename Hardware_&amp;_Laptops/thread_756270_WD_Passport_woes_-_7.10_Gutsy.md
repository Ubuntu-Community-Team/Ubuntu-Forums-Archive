---
title: "WD Passport woes - 7.10 Gutsy"
date: 2008-04-15
forum: Hardware &amp; Laptops
---

### Post by TMC on 2008-04-15
I have a Western Digital 120GB Passport USB hard drive for my laptop and am 
having problems getting it to work.  I am running Ubuntu 7.10 on a Dell Inspiron 
510m.

Using gparted, I have tried formatting the drive to ext2, ext3, Rieser and FAT32 
- of these, only the FAT32 format works.  Although gparted says that the other 
formats succeed, it then reports the drive as an unrecognised format.

I then created a udev rule to get a persistent mount point :

SUBSYSTEM=="block", ATTRS{vendor}=="WD      ", ATTRS{model}=="1600BEV External", NAME="Passport%n", SYMLINK+="%k"

and set up a mount point in /media with the following commands :

sudo mkdir /media/Portable
sudo chgrp plugdev /media/Portable
sudo chmod 774 /media/Portable
sudo chmod +t /media/Portable

If I check the permissions on /media/Portable with the drive unmounted, all is 
as it should be but if I then mount the drive with

sudo mount /dev/Passport1 /media/Portable

and check the properties of /media/Portable, the group has changed to root and 
permissions to 755.  Unmount the drive and it all returns to how I set it.  If I 
mount the drive and go into nautilus as root (either with sudo or su) and try to 
change the permissions or group, I am told that I cannot as I do not have 
permission.

Can you please help?  I don't really mind about the format (although something 
other than FAT would be nice, I can live with it if I have to) but I really do 
need to be able to access this drive.

Many thanks,

David Shaw

---

### Post by roaldz on 2008-04-15
I happen to be the owner of a WD Passport drive too, except mine is 250GB. It works like a charm. I didn´t have to do something for that.. Do you have these problems with other removable storage too?

Roald

---

### Post by TMC on 2008-04-16
I have Seagate FreeAgent and Philips USB hard drives as well.  Both were a bit of a pain to install and the FreeAgent suffers from its well publicised problems with Linux (which I can live with) but neither exhibited the behaviour my Passport is showing

David

---

