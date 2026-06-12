---
title: "Unable to unmount private"
date: 2008-11-01
forum: General Help
---

### Post by Comhra on 2008-11-01
Can't unmount the Private volume in Ibex.  I get an error message saying:/home/user/Private is not in the fstab and you are not root.

Worst bug I've come across.

How do I unmount it?

---

### Post by Cl0ud9 on 2008-11-01
Try using sudo:
```

sudo umount *DirectoryToUnmount*

```

---

### Post by Comhra on 2008-11-01
Tried it

---

### Post by Comhra on 2008-11-01
Got it

---

### Post by Comhra on 2008-11-01
I used force quit, purged it in terminal, then sudo unmount...and deleted the folder with sudo nautilus.

Don't install it...it's as buggy as hell...use true crypt instead.

---

