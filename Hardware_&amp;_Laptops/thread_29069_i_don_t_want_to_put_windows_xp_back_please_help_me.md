---
title: "i don t want to put windows xp back please help me with ubuntu](*,)"
date: 2005-04-22
forum: Hardware &amp; Laptops
---

### Post by oppilif on 2005-04-22
i have installed kubuntu on a compaq presario r3000 (laptop)
every thing works but the cd drive when a put a cd on it and i got to /cdrom it want see anything and i tryid dvd , cd , photo , movies , data but i know that the cd drive 100% works on windows xp if you could help me please because i need to work on this laptop and i don t want to put windows xp back  ](*,)

---

### Post by alastair on 2005-04-22
In the boot log file : /var/log/syslog

You should see mention of any CDROM drive found e.g.

Probing IDE interface ide1...
hdc: TOSHIBA DVD-ROM SD-R9012, ATAPI CD/DVD-ROM drive

This should end up accessible, if a CD is present, under :

/media/cdrom

In fact, if you are in the GUI, it should notice a CDROM in the drive and automount, opening a file browser window. The file /etc/fstab tells the kernel what filesystems to mount and should contain something like :

/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

---

