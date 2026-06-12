---
title: "Internal Hard Drive Permissions"
date: 2007-10-06
forum: Hardware &amp; Laptops
---

### Post by shadder on 2007-10-06
I currently have two internal Hard Drives, sda1 and sdb1. sdb1 has two partitions on it, sdb5 and sdb6. When I first start the computer, neither sdb5 or 6 are showing up on the desktop, but they do show up in the  Places/ Computer list of drives as " 147.3 GB Volume" and "39.0 GB Volume". Both are unmounted and when I attempt to mount them I et a window informing me that access is restricted to system administrators for security reasons and asks for a pasword. When i enter the password they mount fine and show up on the desktob but I'd like to have them mounted at startup.


My current fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7d6ffba1-80e6-4998-bfd8-d64c7f751028 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f8f12cee-ea90-4fed-b263-d2462d864ebc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

If anyone has any suggestions that would be great. Please keep in mind that I'm recently moved over to Linux from XP so simple terms would be helpful...

---

### Post by shadder on 2007-10-06
anyone?

---

### Post by taurus on 2007-10-06
What filesystems are /dev/sdb5 & /dev/sdb6?  Why not add two entries in /etc/fstab to mount them automatically each time you boot Ubuntu?

Post
```
sudo fdisk -l
```

---

### Post by shadder on 2007-10-06
This is what it gave me:

Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9780    78557818+  83  Linux
/dev/sda2            9781        9964     1477980    5  Extended
/dev/sda5            9781        9964     1477948+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2       24321   195350400    f  W95 Ext'd (LBA)
/dev/sdb5               2        5098    40941621   83  Linux
/dev/sdb6            5099       24321   154408716   83  Linux

I'm going to take a guess that that W95 may be a part of the problem?

---

### Post by taurus on 2007-10-06
Okay, since both are ext3, you can edit /etc/fstab 

```
gksudo gedit /etc/fstab
```
and add these two lines to the end of it.

```
/dev/sdb5   /media/sdb5   ext3   defaults   0   1
/dev/sdb6   /media/sdb6   ext3   defaults   0   1
```
Save the changes.  Then, create two new mount points for those two partitions and mount them.

```
sudo mkdir /media/sdb5 /media/sdb6
sudo mount -a
```
And if you want to write to them without using sudo, just change the ownership from root to your login name for both directories.  

_Assuming_ your login name is **shadder**, do

```
sudo chown -R **shadder**:**shadder** /media/sdb5 
sudo chown -R **shadder**:**shadder** /media/sdb6
ls -la /media
```

---

### Post by shadder on 2007-10-06
That worked great! Thanks so much for your help.

---

### Post by ericartman on 2007-10-20
Followed your instructions and all went well, thank you ever so, I HATE fooling with fstab lol
=D>

Cart

---

### Post by Endolith on 2008-05-13
> **taurus said:**
> 
And if you want to write to them without using sudo, just change the ownership from root to your login name for both directories.  

_Assuming_ your login name is **shadder**, do

```
sudo chown -R **shadder**:**shadder** /media/sdb5 
sudo chown -R **shadder**:**shadder** /media/sdb6
ls -la /media
```

Is that the "correct" way to do this, though?  I can go into gksu nautilus and change the permissions for /media/hda1 to Group and Others "Create and delete files", and it works.  Which is better?  What happens on a system with more than one user?

---

