---
title: "Reformatting an internal IDE with Ubuntu on it"
date: 2008-12-07
forum: Hardware
---

### Post by AmunRa on 2008-12-07
This is such a newbie question, but the solution seems not obvious.  I've installed a a 500 gb IDE drive on a computer that already has an 80 gb SATA with the OS on it, and another 500 gb SATA used for storage.  The IDE drive used to be the primary drive for another computer with Ubuntu on it, but i don't care about the contents.  I just want to reformat it, zap, empty.  

Pointers?

---

### Post by taurus on 2008-12-07
Use gparted from the LiveCD to zap it if you wish.

---

### Post by AmunRa on 2008-12-07
I'm using gparted, but from the hard drive. (no, not the same drive as the one i'm trying to reformat)  It has to be from the CD?

---

### Post by taurus on 2008-12-07
As long as the drive is not mounted, you can use gparted from Ubuntu to remove the partitions and reformat it to whatever filesystem you want.

---

### Post by AmunRa on 2008-12-07
Yeah,i just figured that out. . . unmounted. . . duh.  lol.  TYVM :)

---

### Post by howefield on 2008-12-07
So you know which drive you want to format and you know which program to use, what exactly are you stuck with ?

Gparted is pretty simple, load it up and select the drive you want to format.

Edit, yes unmounting helps :)

---

### Post by AmunRa on 2008-12-07
ooook, new issue.  The permissions are set to root, and I can't unlock them.

---

