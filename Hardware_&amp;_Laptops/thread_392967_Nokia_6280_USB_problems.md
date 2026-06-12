---
title: "Nokia 6280 USB problems"
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by andriess on 2007-03-25
I've recently bought a Nokia 6280, and tried to connect it to my PC as a `mass storage device`. It worked fine, until I `safely removed` it. After that my PC just froze on me.  I had to reboot it to get my computer back again. I just more than surprised, how can a USB device kill the OS? If any one has a idea of how to get it fix, please let me know.

Regards
A.
:guitar:

---

### Post by andrew frank on 2007-04-09
i just bought a 6280 as well - and cannot even connect it. how did you do this? any help is highly appreciated!

andrew

---

### Post by davidme on 2007-06-30
To mount I use this :

sudo fdisk -l 

to find out which /dev/ nokia is and then

sudo mount /dev/sde /media/iso/ -t vfat -o iocharset=utf8,umask=000



to unmount I do

sudo umount /media/iso/

Make sure you wait until it fully unmounts it, it can take some time.



note that /media/iso/ is the folder you had to make yourself

sudo mkdir /media/iso

---

