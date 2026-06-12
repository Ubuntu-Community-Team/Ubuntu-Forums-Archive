---
title: "Sony Ericsson memcard read only?"
date: 2009-11-24
forum: Hardware
---

### Post by Tejus on 2009-11-24
Hey! I have a SE K810 with a 2GB memory card. I'm able to view the files on Ubuntu if I connect my phone in file transfer mode, but I'm not able to transfer or delete files as the system is apparently "read only". 

If I try to change this property by right clicking on my memory card in /media and changing the permissions, I get the same error.

How do I enable permissions for it just like those I get for any other usb drive? I deleted my songs from my cell to transfer some new ones, but I'm not able to, so stuck I'm without music!:cry:

---

### Post by Tejus on 2009-11-26
Another problem that seems to be related:

I inserted a VCD disc into the CD drive, Ubuntu asked me what to do with it, I clicked "Open with VLC". VLC gave me an error saying that the movie file is inaccessible. With Movie Player, the error was that the file was read only.

Why is everything on my system Read Only?!

I tried fixing the Memory Card problem by using the chmod command I read about in some other forum, but that didn't work. Same error popped up, that it's a read only file system. sudo'ing the chmod command had no effect either.

Now i'm guessing the actual file "system" in which the memory card is formatted by my phone is not fully supported by Ubuntu. Now does anyone have any clue what I could do, other than switching back to windows (:()?

---

### Post by jacobs444 on 2009-11-26
Give the output of the sudo lsusb (that is Lsusb without caps) in terminal. then the output of the mount command, may be able to help.

---

### Post by Tejus on 2009-11-30
All right...I sent jacobs444 the output (private msg). He suggested:

> /dev/sdc1 on /media/K810I type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,  shortname=mixed,dmask=0077,utf8=1,flush)
/dev/sdd1 on /media/MEMORY CARD type vfat (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000, shortname=mixed,dmask=0077,utf8=1,flush)

one of these should be your memory card
which ever one it is do a:
sudo chown username:username /media/*
sudo chown username:username /media/*.*
sudo chown username:username /media/.*
 #do this exactly as typed, and you should have write permissions to everything currently mounted in media.

Also, double check the write protect switch on the side isn't on.Will try this and get back.

---

### Post by Tejus on 2009-12-01
It was of no avail:

```
chown: changing ownership of `/media/MEMORY CARD/GoogleAppsData': Read-only file system
chown: cannot access `/media/MEMORY CARD/GoogleAppsData': Input/output error
``` for every single file on my mem card.

Going to make a WinXP dual boot now I guess...only solution. Anyway, thanks for looking into it!

---

