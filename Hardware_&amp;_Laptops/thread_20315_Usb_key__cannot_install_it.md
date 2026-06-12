---
title: "Usb key : cannot install it"
date: 2005-03-16
forum: Hardware &amp; Laptops
---

### Post by Frór on 2005-03-16
Hi everyone.

I've recently gotten an USB stick or device. I'd like to use it at work (a ubuntu system). I've got the root access, but I may not abuse it (kernel recompiling, ...). How could I install my key (filesystem is fat32) to get an access to the information on my key in read/write mode ?

Thanx a lot.

---

### Post by lorap on 2005-03-16
hi friend!
do this:
create a folder "usb-ket" in folder "media":
sodo mkdir /media/usb-key
then connect it to the device:
sudo mount /dev/sr0 /media/usb-key -t vfat -o umask=000
have a nice day!
pavel

---

### Post by Frór on 2005-03-16
Great !

This didn't work the way you said, but i had to use /dev/sda1 instead of /dev/sr0 (I've got no /dev/sr0). Now it's great ! Everything works fine.

Thanx a lot

Frór

---

### Post by lorap on 2005-03-16
is your os hoary?
i'm working with warty that's the point.
pavel

---

