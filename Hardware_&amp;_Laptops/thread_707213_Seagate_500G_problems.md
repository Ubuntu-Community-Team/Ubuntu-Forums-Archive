---
title: "Seagate 500G problems"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by Tgon on 2008-02-25
I have recently installed Ubuntu after trying a few other linux distributions.  Ubuntu seemed to work better than the others with the hardware I have on my machines.

The only problem is that I have a 500g Seagate external hard-drive.

When I plug the drive in it is visible in "computer:///" but cannot be accessed, an error comes up saying "could not be mounted".

I've been looking around for a fix for this but cant seem to find one, can anyone help?

---

### Post by Mad_Dawg on 2008-02-25
What I have always done with my external (Maxtor) and thumb drives is plug them into the system before I turn it on.  They are always found when the system boots up.  Not the most convenient solution, but it has always worked for me.

---

### Post by Tgon on 2008-02-27
Yeah, I have a couple of external hard drives, the others work fine its just this one that wont mount, I think theres some kind of compatibility issue but I don't know enough about Ubuntu to fix it.

I looked around on the forums and people seem to have had the same or similar problems with other seagate hard drives but I didn't manage to find a clear fix for it.

If anyone knows about this their help would be great.

---

### Post by froy02 on 2008-02-27
Try installing ntfs-config tool in synaptics.  Once it is installed go to Applications ->System Tools and choose NTFS Configuration Tool.  If you see your drive there put a check mark in the box then click ok.  Another window comes up then check also 'enable read and write on external drives'.

Hope that works for you.

---

### Post by Tgon on 2008-03-06
Thanks, that helped {:0)

the problem now is that I can see the drives contents and access them but I dont have privs to change or add anything.  even as root.

I kind of remember that I could have messed this up while I was still using Vista.  I was sharing it on a network and the privs were wrong.  I started messing with them and they ended up wronger. Basically it went from all people can read and write to nobody can read and write.  the only person with privs is root and still root can only read.

I tried chmod in terminal and it seems even with su privs I dont have the permission to change them.

Anyone know how to fix that?

---

### Post by PmDematagoda on 2008-03-06
Please post the outputs of:-
```
cat /etc/fstab
```
and
```
sudo fdisk -l
```

---

### Post by Tgon on 2008-03-06
**cat /etc/fstab**

dev/disk/by-id/scsi-SATA_FUJITSU_MHW2080_NZ2RT7125R22-part2 /                                      ext3       acl,user_xattr        1 1
/dev/disk/by-id/scsi-SATA_FUJITSU_MHW2080_NZ2RT7125R22-part1 swap                                   swap       defaults              0 0
proc                 /proc                proc       defaults              0 0
sysfs                /sys                 sysfs      noauto                0 0
debugfs              /sys/kernel/debug    debugfs    noauto                0 0
usbfs                /proc/bus/usb        usbfs      noauto                0 0
devpts               /dev/pts             devpts     mode=0620,gid=5       0 0



**sudo fdisk -l**
root's password:
sudo: fdisk: command not found

[B]
Heres a little more info that could be helpful.[/B]

its a 500G seagate mounted to /media/TgonVideo

Owner = Can view content
Group = Forbidden
Others = Forbidden

Owner = tgon
Group = root

Base URL = file:///media/TgonVideo
Device node = /dev/sdb1]

**tgon@DOG:/media> dir**

total 52
drwxr-xr-x 15 tgon root 32768 2008-03-06 00:32 TGONMUSIC
dr-x------  1 tgon root 20480 2008-02-14 20:41 TgonVideo

**tgon@DOG:/media> ls -l TgonVideo**

total 80
dr-x------ 1 tgon root 57344 2007-12-28 20:57 My Documents
dr-x------ 1 tgon root  8192 2007-12-28 20:35 My Uni Files
dr-x------ 1 tgon root 12288 2008-02-13 10:20 New Stuff
dr-x------ 1 tgon root     0 2007-12-18 18:57 $RECYCLE.BIN
dr-x------ 1 tgon root     0 2007-11-27 19:15 RECYCLER
dr-x------ 1 tgon root  4096 2007-12-07 03:10 System Volume Information

**tgon@DOG:/media> chmod a+rw TgonVideo**
chmod: changing permissions of `TgonVideo': Read-only file system
**tgon@DOG:/media> dir**
total 52
drwxr-xr-x 15 tgon root 32768 2008-03-06 00:32 TGONMUSIC
dr-x------  1 tgon root 20480 2008-02-14 20:41 TgonVideo

---

