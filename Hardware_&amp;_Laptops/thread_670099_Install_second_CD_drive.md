---
title: "Install second CD drive"
date: 2008-01-17
forum: Hardware &amp; Laptops
---

### Post by Danyl on 2008-01-17
Hi all

I have installed Ubuntu (Gutsy) and have been using it for a week or so now.

I have another CD-ROM drive I wishe to install in my machine however Ubuntu doesn't know its there (because it wasn't there during installation).

How do I install it now with Ubuntu already installed? I don't have to do a fresh install do I?

---

### Post by ahaslam on 2008-01-17
Does it show in your bios? My Arch install recognised a second hard drive, surely it shouldn't be any different with a cdrom? I'd assume it should show as scd1?
```
sudo mkdir /media/cdrom1
sudo mount /dev/scd1 -t iso9660 /media/cdrom1
```
If you can't access it, try a livecd.

---

### Post by Danyl on 2008-01-17
Thanks guys. All good now after a reboot.

---

### Post by Yellow Pasque on 2008-01-17
Please mark thread as [SOLVED]

---

