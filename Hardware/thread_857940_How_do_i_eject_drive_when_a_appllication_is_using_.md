---
title: "How do i eject drive when a appllication is using it?"
date: 2008-07-13
forum: Hardware
---

### Post by MasterNetra on 2008-07-13
I was wondering how do i force eject the cd drive? I'm trying to install The Sims 2 and as you may know its a 4 cd thing. When it finishes with the first one and requests the second Ubuntu refuses to eject the cd.

---

### Post by matt$2 on 2008-07-13
Check in the file /etc/fstab as to which is the first and which the second.  Bring up a console, enter
sudo eject /dev/cdrom(1 or 2)

and you should succeed.

---

### Post by Yuki_Nagato on 2008-07-13
```
sudo umount -l /dev/XXX
sudo eject /dev/XXX
```

XXX - is the name of your CD-ROM drive.  It could be cd0 or something.

This may lead to errors on the next disk, as you probably ran the installer from the CD-ROM.  If any appear, attempt to move the installer to the desktop.

---

### Post by schuppianer on 2008-07-13
Hi MasterNetra,

the way that workes best in my opinion with installing games is the give the cdrom-drive a direction like in windows (D:) or so, u do this in the wine config, run
```
winecfg
``` go to "devices" and give your /media/cdrom0 	character D: then you can eject it every time with
```
wine eject d:
```

Schuppianer

---

