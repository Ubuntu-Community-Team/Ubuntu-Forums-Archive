---
title: "Help with packaging - control file not found"
date: 2009-10-25
forum: Installation &amp; Upgrades
---

### Post by Gordonisnz on 2009-10-25
Hi,

Ive created a file /mypackage/DEBIAN/control

and doing the following command (I've tried as my username & as root)

> 
root@gordon-desktop:/mypackage/DEBIAN# ls
control  control~  mycool  preinst~

root@gordon-desktop:/mypackage/DEBIAN# dpkg --build mypackage ./
dpkg-deb: failed to open package info file `mypackage/DEBIAN/control' for reading: No such file or directory
root@gordon-desktop:/mypackage/DEBIAN# 


Ive also changed directories, & re-tried the dpkg command - same thing.


any advise as to why it can't find the file ?

---

