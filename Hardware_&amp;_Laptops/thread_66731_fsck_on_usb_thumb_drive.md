---
title: "fsck on usb thumb drive"
date: 2005-09-18
forum: Hardware &amp; Laptops
---

### Post by geoffr on 2005-09-18
With 5.04 or 5.10, you insert the thumb drive and the icon pops up. 

At this point you can't run fsck, because the device is mounted.

So you unmount. But then you can't run fsck because the device (e.g., /dev/sda1)
doesn't exist.

How does one fsck a thumb drive?

Cheers,
Geoff Russell

---

### Post by geoffr on 2005-09-18
Gotit.

System->Preferences -> Removable drives and Media

Adjust to NOT mount on insertion.

Device is created but not mounted and fsck then runs fine.

 O:) 

Geoff

---

