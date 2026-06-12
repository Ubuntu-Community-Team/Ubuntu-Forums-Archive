---
title: "Automatically mounting my other drives on bootup?"
date: 2007-05-24
forum: Hardware &amp; Laptops
---

### Post by last1 on 2007-05-24
I had this working, but did some update and now it's not, and don't remember what I did to get it like that in the first place. I have a second hard drive that I need to be mounted before I log into the desktop. 
fstab lists it as this
# /dev/sda1     /media/disk     ext3,auto       errors=remount-ro 0
/dev/sda1 /media/disk auto users,noauto,atime,auto,rw,nodev,exec,nosuid 0 0

So what's the deal, any suggestions?

---

### Post by benanzo on 2007-05-24
you need to remove "noauto" from the fstab options
You have "noauto" before  "auto" listed.  It will default to the first option if conflicting options are given.

the way it is now:
```
/dev/sda1 /media/disk auto users,_noauto_,atime,auto,rw,nodev,exec,nosuid 0 0
```
the way it should be:
```
/dev/sda1 /media/disk auto users,atime,auto,rw,nodev,exec,nosuid 0 0
```

---

### Post by Goombie on 2007-05-24
Would that code work to automount any disk, as long as I changed the paths? I had a line in fstab to automatically mount the partition I keep my documents in, but it always changed the permissions to rwxrwxrwx, which affected another program in odd ways.

---

### Post by last1 on 2007-05-24
That did the trick, thanks bro. It's workin like a charm now.

---

