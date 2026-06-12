---
title: "Phantom USB drive"
date: 2009-04-28
forum: Hardware
---

### Post by ociosu on 2009-04-28
Hi!

Today I noticed that my USB pendrives were not automatically detected.

When checking the removable devices in the menu bar, I can see a USB drive that does not exist.
When connecting a real usb drive, I can see there two USB drives, the real one, and the phantom one....
But I can not see anything new in the desktop.

None of them can be explored...

I can not see anything changing at /media when connecting or disconnecting the usb drive.

There is no phantom drive there....

Any idea?

Thanks!

---

### Post by ddrichardson on 2009-04-29
Yes, try:```

sudo echo usb_storage >> /etc/modules
```

---

### Post by ociosu on 2009-04-30
Thanks for your answer.
/etc/modules
access denied

---

### Post by ddrichardson on 2009-04-30
OK edit it manually```
gksudo gedit /etc/modules
```and add the line```

usb_storage
```

---

### Post by ociosu on 2009-04-30
Thanks!

The main problem is solved. Now if I plug a usb stick, it is detected, and works normally.

But the "strange" USB unit is still there.
It is like a windows shortcut, that takes nowhere.
It is shown in the menu bar, and in nautilus too, but if I click on it nothing happens.


I followed your instructions. Restart X. USB device still there...
Reboot, and USB device still there.

The file looks like this now:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
usb_storage


Thanks again!

---

### Post by ddrichardson on 2009-04-30
For the "phantom" drive, can you post:```
sudo fdisk-l
```

---

### Post by ociosu on 2009-05-01
I really don't understand all the messing of drives here...

I just have 3 hd
First one has (or should have) three partitions: data, xp, and linux

I can see a 6Gb "linux" partition I don't know what it is for, neither why it is there...
I guess is something wrong, that had never bothered me too much anyway...

And two swap partitions, I guess it is something related with the previous "linux" partition.

Phantom drives are my speciality...

Sencond and third hd are just data backups



Disco /dev/sda: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x17b817b8

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1       19929   160079661    7  HPFS/NTFS
/dev/sda2           19930       40375   164232495    7  HPFS/NTFS
/dev/sda3           40376       60801   164071845    f  W95 Ext'd (LBA)
/dev/sda5           40376       41171     6393838+  83  Linux
/dev/sda6           41172       59754   149267916   83  Linux
/dev/sda7           59755       60546     6361708+  82  Linux swap / Solaris
/dev/sda8           60547       60801     2048256   82  Linux swap / Solaris

Disco /dev/sdb: 500.1 GB, 500107862016 bytes
255 cabezas, 63 sectores/pista, 60801 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x5bc1a41f

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disco /dev/sdc: 80.0 GB, 80026361856 bytes
255 cabezas, 63 sectores/pista, 9729 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xcc99cc99

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1   *           1        9729    78148161    7  HPFS/NTFS

---

