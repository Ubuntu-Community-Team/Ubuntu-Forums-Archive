---
title: "Floppies stopped auto-mounting!"
date: 2007-02-22
forum: Hardware &amp; Laptops
---

### Post by darundal on 2007-02-22
For some reason, my computer has stopped mounting floppies when I insert them in the floppy drive. I found this thread 

[http://ubuntuforums.org/showthread.php?t=136046](http://ubuntuforums.org/showthread.php?t=136046)

but they don't offer anything that helps me fix the issue of the floppy not automatically mounting (although this command from the thread sudo mount -t msdos /dev/fd0 /media/floppy does work after I created the floppy folder in media). I honestly have no idea whatsoever how to even start to fix this. Can anyone offer any help?

---

### Post by blazerte on 2007-04-24
Bump - Same problem here with a new Feisty install.

The problem is with the kde daemon and /media/floppy0 object in Konquerer's "Storage Media". 

Automount only works if I first right click on the desktop and create a permanent link to the floppy device, But even then the object in Konquerer's "Storage Media" is not updated with a new icon when a floppy is inserted.

Creating a permanent desktop link is not necessary for cdroms. They automount fine without it. A link to the device is created automagically on the desktop by the KDE daemon whenever a cdrom is put in and the object in Konqueror's Storage Media is updated as well.

fstab looks good:
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/media/floppy0 is there

???

---

### Post by setyawan111 on 2007-05-15
Dear All, 

I have still problem about mounting FDD.

My MB Jetway chipset VIA (P4M2PROC)
I/O chip Fintek F71805FG.
The MB cannot mount automatic FDD.

If I change to another brand like ECS, PC-Chip, Esys , FDD (floppy) can detect automatic.

I have try manual mounting.. but still cannot detect FDD.

regards


setyawan

---

