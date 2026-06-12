---
title: "Unable to GParted LaCie 500GB External USB Drive"
date: 2008-01-01
forum: Hardware &amp; Laptops
---

### Post by manville on 2008-01-01
I have a 500GB LaCie External Drive (Drive is USB2.0 but connected via USB 1.1). It is formatted as fat32 (vfat) but I want to add a ext2/3 partition to it. Running GParted with drive mounted shows the partition, locked, but if I attempt to unmount it to modify it GParted just gets stuck scanning all devices. Is there a problem with unmounting that is easy to solve? or should I abandon this plan? I have tried using latest LiveCD but same effect.

---

### Post by logos34 on 2008-01-01
System>Prefs>Removable Drives and media>storage tab>uncheck all.

Now try to unmout it in gparted.  Or in terminal:

sudo umount /media/disk 

or wherever it's mounting

---

