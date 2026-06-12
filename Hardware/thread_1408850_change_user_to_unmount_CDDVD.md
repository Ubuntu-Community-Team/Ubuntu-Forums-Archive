---
title: "change user to unmount CD/DVD"
date: 2010-02-16
forum: Hardware
---

### Post by dr_saaron on 2010-02-16
I've recently installed Ubuntu.  I've noticed that if I put in a DVD or CD when multiple users are logged into the system, I usually have to change users to unmount the disk.  If I try to unmount or eject under my own user ID, the ID under which it was first mounted, I get the error message saying only the other user can remove it.  How do I fix this?

---

### Post by TitanusEramius on 2010-02-17
This is not an actual solution but another approach, have you tried:
```
sudo umount /dev/sd**
```where sd** being the dvd-rom (like sdc1 or sdb1)

---

### Post by jsaulters on 2010-05-05
I used to have this problem, too. I believe you just need to modify your /etc/fstab file.  In the options for your cdrom drive, change "user" to "users" 

Here is the relevant output from my fstab file.  I hope this helps.



# /etc/fstab: static file system information. 
# 
# <file system> <mount point>   <type>      <options>              <dump>  <pass> 

/dev/scd0       /media/cdrom0   udf,iso9660 users,noauto,exec,utf8 0       0

---

### Post by dr_saaron on 2010-05-07
BTW, this doesn't seem to be an issue with Lucid.  At least I haven't had any problems with it since upgrading.

---

