---
title: "Having problems mounting devices"
date: 2006-05-10
forum: Hardware &amp; Laptops
---

### Post by nbpetts on 2006-05-10
I recently recompiled my kernel, but now i cannot mount my 2nd hard drive or my ipod or my usb flash drive.  I can see them in disks managers, but they are all listed as inaccessable.  Fdisk -l only shows the usb drive and the ipod, but they wont mount.  When i do sudo mount -a, i get 

mount: /dev/hdb1 already mounted or /media/win busy

any ideas?

---

### Post by louis_nichols on 2006-05-11
what do you get if you simply type mount?

Maybe it's really already mounted...

---

