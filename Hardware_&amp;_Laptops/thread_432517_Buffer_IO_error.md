---
title: "Buffer I/O error"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by Alex N on 2007-05-04
It happens SOMETIMES. Applications refuses to work, system is unstable
and the following text appears in console :

Buffer I/O error on hdb1

hda  is Maxtor IDE 100GB with Win
hdb is Quantum 30GB with Linux.

fsck on hdb revealed no bad blocks.

After poweroff everything works again, even applications that did not work
when this error occurred.

---

### Post by klytu on 2007-05-07
> **Alex N said:**
> It happens SOMETIMES. Applications refuses to work, system is unstable
and the following text appears in console :

Buffer I/O error on hdb1

hda  is Maxtor IDE 100GB with Win
hdb is Quantum 30GB with Linux.

fsck on hdb revealed no bad blocks.

After poweroff everything works again, even applications that did not work
when this error occurred.

Your problems MIGHT be hardware-related. The two main places I would suggest you check are your RAM and your power supply. You can run memtest from the GRUB menu overnight to see if it reports any problems with your RAM. I mentioned the power supply because I had similar issues just before my last power supply failed completely ...

---

