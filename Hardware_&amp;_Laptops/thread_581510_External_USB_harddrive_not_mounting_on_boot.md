---
title: "External USB harddrive not mounting on boot"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by satbunny on 2007-10-19
Hi. Xubuntu 7.10. I have an external USB drive, a Seagate.

When I reboot my PC (usually only after a power cut) the external drive doesn't mount.
This is despite being in my fstab..

Gnome Partition Editor (gparted) reports the external drive as sdd, so I added it to my fstab as follows:

> /dev/sdd1	/media/disk	ext3	defaults	0	0

I can mount it using gparted and also manually, but it'd not working on boot up.. and yes I have ensured that the USB drive is on before the PC..

Have I made a mistake in the fstab?

---

### Post by ddrichardson on 2007-10-20
add auto after defaults:```
/dev/sdd1	/media/disk	ext3	defaults,auto	0	0
```

---

### Post by satbunny on 2007-10-21
Thanks

---

