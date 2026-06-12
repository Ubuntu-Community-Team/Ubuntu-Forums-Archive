---
title: "Trying to resize again."
date: 2008-11-27
forum: General Help
---

### Post by Arukas on 2008-11-27
When I first installed ubuntu, I gparted was used to resize my harddrives.  I would like to resize a second harddrive, so Ubuntu can store files on it easily.  But gparted isn't cooperating with me.  Most of the commands are greyed out, and its not giving me a reason either.

Anyone know how to handle this problem?

---

### Post by donbenjy on 2008-11-27
HAve you unmounted the volume?  Right click on the partition that you want to format and clikc unmount, then you should be able to resize it.

To mount the drive again, open a command line and type:
```
sudo mount -a
```

Hope that helps!

---

### Post by Arukas on 2008-11-27
I didn't type that command, i just unmounted it by clicking on it and selecting unmount.  Is that the same thing?  Because there's no sudo the way I unmount it.

---

### Post by Arukas on 2008-11-29
I misread what you said.

Okay, I already tried unmounting the harddrive I want to resize, and it doesn't let me.  The hard drive isn't the same one that Ubuntu is on, its a second one.

---

### Post by Arukas on 2008-11-30
Has anyone tried to resize a second hardrive for ubuntu using gparted?

---

