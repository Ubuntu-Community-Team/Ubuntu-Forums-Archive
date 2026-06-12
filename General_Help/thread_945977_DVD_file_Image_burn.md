---
title: "DVD file Image burn"
date: 2008-10-12
forum: General Help
---

### Post by Vertoxic on 2008-10-12
what is a good program to burn image files on to a dvd?

---

### Post by Julius1988 on 2008-10-12
Try Brasero or K3B

---

### Post by yabbadabbadont on 2008-10-12
If they are image files of video dvds, then you can easily do it in a terminal window with the following command:
```
growisofs -dvd-compat -Z /dev/dvd=NameOfYourImageFile
```
This assumes that "dvd+rw-tools" is installed.  (it usually is)

If they are not video dvd images, but just a regular data dvd image, then use the same command, but leave out the "-dvd-compat" option.

---

### Post by Vertoxic on 2008-10-12
this is for dvd data :)

---

### Post by Vertoxic on 2008-10-13
any?

---

### Post by yabbadabbadont on 2008-10-13
I gave a command that will work.  As I said, leave out the "-dvd-compat" and it will work fine for an image of a data dvd.

---

