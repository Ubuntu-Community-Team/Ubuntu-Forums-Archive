---
title: "Packard Bell PC - CD Drive Button not working"
date: 2007-04-01
forum: Hardware &amp; Laptops
---

### Post by Marc_UK on 2007-04-01
I have just switched to the Ubuntu 7 Beta and Everything works! The Sound, graphic card, (although I would prefer a bigger resolution then 1024) Logitech Quickcam and even the card reader!

Just one problem, the cd drive doesnt work when I press a button, it works fine under windows.

---

### Post by spin2cool on 2007-04-01
Ubuntu operates under teh same principle as macs - you have to right click on the CD drive and choose Eject to remove a CD.

---

### Post by Marc_UK on 2007-04-03
Well the CD Drive can't even be opened that way. I right click and that and it says unable to unmount.

---

### Post by spin2cool on 2007-04-03
if it can't unmount, you need to do two things

1) first, make sure any programs that may be accessing files on the CD are closed.  Try again.

2) If that doesn't work, you can do a lazy unmount by typing
```
umount -z /media/cdrom
```
(or cdrom0, depending on your system)

---

### Post by spin2cool on 2007-04-03
my bad - the lazy command switch should be '-l', not -'z'
so 

"umount -l /media/cdrom/"

---

### Post by Marc_UK on 2007-04-04
Thanks for you help mate, but I have tried them both and still had no luck.

---

### Post by seodavid on 2007-11-07
> **Marc_UK said:**
> I have just switched to the Ubuntu 7 Beta and Everything works! The Sound, graphic card, (although I would prefer a bigger resolution then 1024) Logitech Quickcam and even the card reader!

Just one problem, the cd drive doesnt work when I press a button, it works fine under windows.

I have same prob under windows :lolflag: (Im starting to resent there pre-installed software 2)

anyway, the one I have requires drivers, as its not physically connected to the disk release button, i resolved this with using a diff case.

(ps reason i did not build this pc, was it was a low budget quick fix, one that did not work either! lol it still does not shut down - "The joys of Vista")

---

