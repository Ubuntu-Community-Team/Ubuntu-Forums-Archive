---
title: "Stop locking the CD drive!"
date: 2008-05-10
forum: Hardware
---

### Post by irinotecan on 2008-05-10
So this is rather annoying.  I am trying to install a Windows program using WINE.  It has multiple CDs.  Setup runs fine, copies the first CD, then prompts to insert CD 2. Press eject on the CD drive.  What happens?

```
Cannot unmount volume
An application is preventing the volume '<volume name>' from being unmounted.
```

AARGH!  So I'm in a catch-22:  I can't unmount/eject the volume without killing /media/cdrom0/setup.exe, but I need setup.exe running to install the remaining CDs!

Doing a 'sudo umount -f /media/cdrom0' is no help either:
```
umount2: Device or resource busy
umount: /media/cdrom0: device is busy
umount2: Device or resource busy
umount: /media/cdrom0: device is busy
```

So how do I stop Gnome/Automount/Linux kernel from locking the CD drive and preventing me from swapping install CDs?????

---

### Post by Rocket2DMn on 2008-05-10
I have found that sometimes if a disk gets locked up, using the -l option with umount will allow it to disconnect (lazy unmounting).  It may not work since the program is actually still running, but it's worth a shot.

---

### Post by irinotecan on 2008-05-10
That did it, Thanks!

---

