---
title: "External Hardrive not working"
date: 2008-08-30
forum: Hardware
---

### Post by mojo123 on 2008-08-30
When ever i go to my external hard drive (WD Passport), i get a message saying "You are not privileged to mount the volume "WD Passport". I tried entering it through "gksudo nautilus", but i get another error saying "Unable to mount the volume "WD Passport fuse:failed to access mountpoint /media/ hd-nfts:No such file or directory.

My hd is formated as NFTS.

---

### Post by rabbitEars on 2008-08-30
I'm having trouble accessing my external in Ubuntu as well.  It's not a WD Passport, rather a Calvary, but NTFS-formatted like yours.  And I think that's the root of the problem: the default filesystem for Linux is ext3, not NTFS ([https://help.ubuntu.com/8.04/hardware/C/disks.html](https://help.ubuntu.com/8.04/hardware/C/disks.html)).  Maybe the external has to reformatted to be Ubuntu-accessible?

---

### Post by gmxgeek on 2008-08-30
[http://ubuntuforums.org/showthread.php?t=905122](http://ubuntuforums.org/showthread.php?t=905122)

---

### Post by rabbitEars on 2008-08-30
Scratch what I said before because Linux can read NTFS.  I'm still learning about formatting.

---

### Post by gmxgeek on 2008-08-30
yeah, linux can basically read everything :)

Just make you mount the drive using one of the two methods in the other thread

---

