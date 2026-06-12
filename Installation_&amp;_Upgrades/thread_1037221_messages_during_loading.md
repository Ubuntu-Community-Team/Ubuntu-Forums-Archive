---
title: "messages during loading"
date: 2009-01-11
forum: Installation &amp; Upgrades
---

### Post by ANew on 2009-01-11
There are a lot of messages during loading of ubuntu.
Any idea how to illiminate them.

After i installed ubuntu it was slow loading but without
messages, them i resized the partition with ubuntu and
after then got whole screen of messages during loading.
"done, doene...."


Related question if there is a way to illimitate
"ISOLINUX 3.38...." message during loading

---

### Post by taurus on 2009-01-11
Look in /boot/grub/menu.lst and make sure you have **quiet splash** at the end of the _kernel_ line.

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by ANew on 2009-01-11
> **taurus said:**
> Look in /boot/grub/menu.lst and make sure you have **quiet splash** at the end of the _kernel_ line.

```
gksudo gedit /boot/grub/menu.lst
```

Yes i have it, i have not changed the initial setup.
As i said there were no messages before resizing of partition
and resizing of partions had not changes menu.lst file

---

### Post by taurus on 2009-01-11
Check the UUID to make sure it is still the same for / in /etc/fstab & /boot/grub/menu.lst.  Resizing it could alter the UUID.

```
sudo blkid
```

---

