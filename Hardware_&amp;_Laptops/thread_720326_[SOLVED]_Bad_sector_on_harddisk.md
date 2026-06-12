---
title: "[SOLVED] Bad sector on harddisk"
date: 2008-03-10
forum: Hardware &amp; Laptops
---

### Post by reyhan on 2008-03-10
how do i check bad sector on harddisk?

---

### Post by jmate24 on 2008-03-10
```
sudo tune2fs -c 1 /dev/xxxx
``` where xxxx can mean hda1 or sda1. that will check it every boot and then it should clear out and mark the bad sectors as bad.

---

### Post by Rocket2DMn on 2008-03-10
If you don't want it to check at every boot after doing that, run it again with "30" as the number option which should be the default for Ubuntu.
```
sudo tune2fs -c 30 /dev/xxxx
```

An alternate option that will force it to check the next time you reboot is
```
sudo touch /forcefsck
```
Creating the forcefsck file in the root of your filesystem tells it to check on your next boot.  Either way, you will have to reboot to check since fsck can't check a filesystem that is mounted.

---

