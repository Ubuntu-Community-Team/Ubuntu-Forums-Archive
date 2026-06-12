---
title: "Hdd Usb"
date: 2005-03-10
forum: Hardware &amp; Laptops
---

### Post by Viggy on 2005-03-10
Hi!

I'm new in ubuntu.. and i like it!

So, i have a little problem... I can't mount my external hdd nor my usb pen... my first problem is that i don't have /dev/sda* it is normal?

The solutions i found on the internet uses this device.

Thanks in advance,
Tiago Bernardo

---

### Post by lorap on 2005-03-11
hi friend!
do the next:
i.create folder:

sudo mkdir /media/yourusbhd

ii.add a line to the /etc/fstab file:

ii.i.sudo nano /etc/fstab(opens it)
ii.ii./dev/sda0       /media/yourusbhd udf,iso9660 rw,user,noauto 0 0(add this line)

that should be enaugh
to save changes ctrl+o
to exit ctrl+x
have a nice day friend!
pavel

---

