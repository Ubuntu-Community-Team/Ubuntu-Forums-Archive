---
title: "Creative zen xtra usb"
date: 2005-03-04
forum: Hardware &amp; Laptops
---

### Post by LK_gandalf_ on 2005-03-04
Hi, anyone know hot to make this mp3 player works under ubuntu?

thanks! i'm a newbies

---

### Post by JmSchanck on 2005-03-04
Gnomad 2 is a nice little project for getting the Creative mp3 players working on linux check it out right here: [http://gnomad2.sourceforge.net/](http://gnomad2.sourceforge.net/)

Install instructions and how to get everything set up are there. Good luck :)

---

### Post by Stefan Koopmanschap on 2005-03-16
Does anyone know if it's possible to simply mount the device without any additional software, like an external storage device? With digital camera's this is simple by mounting /dev/sd* but for some reason the Zen does not get an entry in /dev/sd* ... I'm having a hell of a hard time installing gnomad2 or any of the other similar apps due to dependency problems in the Ubuntu repositories.

---

### Post by lorap on 2005-03-16
is it an external one?
pavel

---

### Post by Stefan Koopmanschap on 2005-03-16
[QUOTE=lorap]is it an external one?
pavel[/QUOTE]

yeah, it's a regular portable mp3 player by Creative. It has a USB connection for transferring files from and to the player.

---

### Post by lorap on 2005-03-16
hi again friend!
i'll do my best to help you as other people helped me.
lets try to mount your device.
i'm working with warty so in me case the device name's SR0,
but in the case of hoary it could be either SCD0 or SCD1.
check and tell me if none of these were found.
but if they are present then do this:

create a directory PLAYER in /MEDIA this way:

sudo mkdir /media/player

after what lets connect your player to the divece:

mount /dev/scd0 /media/player -t vfat -o umask=000

let me know if it did help.
pavel

---

### Post by steffen on 2005-04-03
Some of the Creative players are made not to mount as a disk, other than through Creative's interface. When sticking my Creative Zen into my laptop, my syslog has a message about /dev/tp2 or something - don't know what that could be...

However, Gnomad2 should work

---

