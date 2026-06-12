---
title: "cannot unmount USB device"
date: 2008-03-03
forum: Hardware &amp; Laptops
---

### Post by dhap on 2008-03-03
I cannot unmount a USB device  from nautilus, it keeps complaining:
Cannot unmount volume
An application is preventing the volume 'XXX' from being unmounted.

I do not have any application open other than nautilus, or none I know that is using the USB device. 

Using

sudo  umount /media/XXX 

gives me:

umount: /media/XXX: device is busy

What do I do to find out which application is preventing XXX ?

---

### Post by erginemr on 2008-03-03
Such a command
```
lsof | grep -i /media/disk
```
may unveil the name of the application that keeps your drive busy.

---

### Post by mrsteveman1 on 2008-03-03
I've noticed this with samba sometimes on a server here, even if no one is actually doing anything over the network samba still has files open and thus prevents the drive from being unmounted.

---

### Post by dhap on 2008-03-04
lsof | grep -i /media/disk

did not return anything, but trying to unmount from nautilus gave me an error
'cannot eject volume'

The 'umount' command from terminal worked though.

---

### Post by erginemr on 2008-03-04
You should have tried:
```
lsof | grep -i /media/<your_removable_disk>
```
as in
> /media/XXX

---

### Post by dhap on 2008-03-04
yes, that is what I tried.

---

