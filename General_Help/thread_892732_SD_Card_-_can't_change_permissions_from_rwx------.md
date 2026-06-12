---
title: "SD Card - can't change permissions from rwx------"
date: 2008-08-17
forum: General Help
---

### Post by EricDB on 2008-08-17
I have an SD card I use in my digital camera.  All files on the card have by default rwx --- --- permissions.  This is a pain, because I usually just copy straight from the card to my home network storage.  Then my wife can't look at them, unless I remember to chmod them manually.

I've tried changing permissions on the mount point, and on the individual files/directories on the card, but it doesn't work, whether I do it as root or as myself (I have ownership of the mount point).  The command doesn't give an error, but the permissions don't change.  For reference, I've tried "chmod 777 <file>" and "chmod a+rwx <file>".

How can I get those files to default to world-readwriteable?

---

### Post by fragos on 2008-08-17
Windows FAT doesn't have permissions so rwx owner are assumed by default. You can transfer the files to a native Linux partition and change the folder and contents to rw.

---

### Post by EricDB on 2008-08-17
Yeah, that's what I've been doing...but it's easy to forget and just copy them straight to the network storage, where they're visible but unreadable to anyone but me.

I was hoping there was a way to change the assumed permissions for FAT32 or something...

---

### Post by EricDB on 2008-08-17
I've found the problem setting, but I don't know how to change it.  Here's the mtab line for that mount:

```
/dev/mmcblk0p1 /media/CANON_DC vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
```

It's that "umask=077" that's messing me up.  I want to make it 000, but I don't know where to change it--there's no fstab line for the memory card reader (the built-in reader on my Dell XPS m1210 laptop).

Anyone know where I can change that?

---

### Post by fragos on 2008-08-17
udev  rules cover the mounting of USB devices. I think that's where you should look.

---

