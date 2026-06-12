---
title: "[SOLVED] Usb disk beeps when HAL is on"
date: 2008-01-09
forum: Hardware &amp; Laptops
---

### Post by jesse5143 on 2008-01-09
My usb disk beeps every other second, but if i do

sudo /etc/init.d/hal stop

then it stops. But i guess thats not the best way to fix the problem.

Any ideas?

//Jens

---

### Post by jesse5143 on 2008-01-09
No not really it makes sounds then, but now its sounds like roadrunner(beep-beep) but only one beep :).

Well, yesterday i had i mounted in  /media/usbdisk and on the disk i hade folders like, school, video, downloads. And in my home folder i had sym links to each of them.

Today i have rearrange things and maked my home partition and the usb disk to a logical volym(lvm) mounted at /home so my home is a part of the internaldisk and the whole usbdisk. But i had these noises yesterday too. 

Also it seems it doesn't stop completely when stopping hal, say it was every 10 seconds before then it beeps maybe every 15-30 min when hal its stopped.

---

### Post by jesse5143 on 2008-01-28
Seems like fschk did the trick, havent got an beep since.

---

