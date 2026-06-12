---
title: "intel graphics"
date: 2009-04-15
forum: Hardware
---

### Post by bigern83 on 2009-04-15
Hi,  

Im having real issues getting my graphics drivers to work correctly, I have a sony vaio vgn-n21m which has an Intel Graphics Media Accelerator 950 graphics chip, my xorg log says its using the i810 module which i believe is the wrong one and I do not know how to change it. 

I have no 3d graphics support at the moment, Ive been trying to sort this for a long time now and Im just not getting anywhere.

If anyone knows what I need to do help would be massively appreciated. 

Regards

---

### Post by Psychopump on 2009-04-16
I´ll be following this thread...
Similar issues here (but also plenty of other threads concerning it).

---

### Post by Daisuke_Aramaki on 2009-04-16
If i am right, i810 is part of the Xorg meta package that comes with the installation. Ever since xf86-video-intel2.1 or so, support exists for your chipset. I use a source based distro, so when i compiled Xorg, i was given the option of using the right driver. I will look up my install logs tonight and get back to you.

---

