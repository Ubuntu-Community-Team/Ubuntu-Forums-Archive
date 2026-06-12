---
title: "the attempt to mount filesystem ext3 failed"
date: 2009-04-02
forum: Installation &amp; Upgrades
---

### Post by einfinger on 2009-04-02
Im getting this error when i try to install 8.10 64bit.. any ideas ?

---

### Post by taurus on 2009-04-02
Did you install Ubuntu, intrepid, on it own (separate) partition or did you install it from windows?

Boot with Ubuntu LiveCD and then post the output of this command from a terminal.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by einfinger on 2009-04-02
its a clean install.

and for some reason sudo fdisk -l gives me an error about not finding sda1

---

### Post by taurus on 2009-04-02
Could be a problem with the harddrive.  Go into the BIOS and see if it's listed in there.

---

### Post by einfinger on 2009-04-02
the disk is there, it finds it during installation aswell. its when i start the installation after choosing partitions and such that the error occurs.

---

### Post by einfinger on 2009-04-02
this is weird, i get the same error when trying to install linux mint :o

---

