---
title: "[SOLVED] NTFS-3G Problem"
date: 2008-02-05
forum: Hardware &amp; Laptops
---

### Post by pikitsan on 2008-02-05
Hi i installed ntfs-3g but i can't mount my pata disk.The disk that has ubuntu it's ok.When i configure the fstab and the settings from ntfs-config it says:

> Mounting /media/hdb1 failed.

Hibernated non-system partition, refused to mount.
Failed to mount '/dev/disk/by-uuid/06DC287CDC28685F': Operation not permitted
The NTFS partition is hibernated. Please resume Windows and turned it 
off properly, so mounting could be done safely.

I resume windoze blah blah but nothing happened. :( Can anyone help me ???

Regards. :)

---

### Post by aysiu on 2008-02-05
It all looks like gobbledygook to me, but you may find [this](http://osdir.com/ml/file-systems.ntfs.devel/2005-04/msg00023.html) helpful.

---

### Post by szaka on 2008-02-06
The latest NTFS-3G BETA driver supports the hibernated NTFS scenario. There are more info here: [http://forums.fedoraforum.org/forum/showpost.php?p=956335&postcount=3](http://forums.fedoraforum.org/forum/showpost.php?p=956335&postcount=3)

---

### Post by pikitsan on 2008-02-07
PROBLEM SOLVED !!!!!!! Thank you guyssssss.

can any of the mods mark the thread as solved ??thx :)

---

