---
title: "No puedo recuperar usb con Ubuntu"
date: 2023-11-25
forum: Hardware
---

### Post by serv4ndo on 2023-11-25
Hola, ten una usb con ubuntu qué utilicé para instalarlo, el problema es que ahora no puedo formatear esa usb para utilizarla en otras cosas, he intentado de todo, con windows, con la propia aplicación de disks, con gparted pero no me funciona, agradecería mucho su ayuda. Gracias.

---

### Post by yancek on 2023-11-25
If you used a usb to put an Ubuntu iso on it for the purpose of installing Ubuntu and now want to use that usb for some other purpose, storing data for example, you will need to creat a new partition table on the device.  That will delete all data on the usb.  You can do this with Gparted by clicking on the Device tab at the top of the page and selecting Create Partition Table.

---

### Post by serv4ndo on 2023-11-25
Intento eso pero me dice "can't write to /dev/sdb, because it is opened read-only".

---

### Post by yancek on 2023-11-26
You need to do this (run gparted) from another device drive and make sure your 'sdb' is not mounted before trying this.

---

### Post by serv4ndo on 2023-12-02
Intento hacer eso pero de nuevo me da un errror.
[https://drive.google.com/file/d/14yhGOSVgO9rPMaE7wrp0WeIFxnvNHGGG/view?usp=sharing](https://drive.google.com/file/d/14yhGOSVgO9rPMaE7wrp0WeIFxnvNHGGG/view?usp=sharing)

---

### Post by yancek on 2023-12-03
That is not an error, but is informational.  Writing a new partition table will overwrite the iso on the usb as I explained above in post 2.  Until you do that, the usb will not be usable for other ;purposes.  It is possible to put a Linux iso on a usb and have a separate partition for data but that is a different, more complicated method and not the one you used.

---

