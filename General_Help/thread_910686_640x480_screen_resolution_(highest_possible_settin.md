---
title: "640x480 screen resolution (highest possible setting)"
date: 2008-09-04
forum: General Help
---

### Post by drivewaycat on 2008-09-04
Hi, I just recently started using Ubuntu (8.04) and I was trying to see if it recognized my graphics card. I went to the Hardware Drivers window to see "No proprietary drivers are in use on this system" and that nothing showed up in the dialog box. I went to the screen configuration and graphics card utility, and I chose the driver that matched my graphics card (ATI Rage 128 ). Upon relogging in, my resolution is now set at a terrible 640x480, and I can't seem to get it any higher than that. Help?

---

### Post by easybake on 2008-09-04
You can install envy. It can install the latest drivers for nvidia or ati. 
Open up Accessories>Terminal 
paste this```
sudo apt-get install envyng-gtk
```
when its done installing, to run it, in terminal type ```
envyng-gtk
```

When it opens choose ati and click ok. it should take care of the rest for you.

---

### Post by Kinetic_lord on 2008-09-05
easybake is right, i had the same problem... get Envy and install your graphics card, everything will be all right after... even the compiz fusion :D

---

### Post by drivewaycat on 2008-09-05
Thanks! I did as you suggested and my resolution is at 800x600 now - much better than before. It was higher before I screwed it up - is it possible that the driver found for my graphics card is fairly old (my card is old too) and so that is why I can't set higher than 800x600?

---

### Post by easybake on 2008-09-05
> **drivewaycat said:**
> Thanks! I did as you suggested and my resolution is at 800x600 now - much better than before. It was higher before I screwed it up - is it possible that the driver found for my graphics card is fairly old (my card is old too) and so that is why I can't set higher than 800x600?

If that worked you should be able to go into your normal display settings and change it to a higher resolution.

---

### Post by drivewaycat on 2008-09-06
I tried that - the highest resolution that I can choose is 800x600.

---

### Post by diobrando on 2008-09-07
can you post your /etc/X11/xorg.conf? Rage 128 should be able to use the 'r128' driver.

---

### Post by Joeb454 on 2008-09-07
Moved to General Help

---

### Post by lost_soul on 2008-09-07
try going to screens and graphics once again, but this time change the screen choose another one with a higher resolution.

---

### Post by ruderbecca on 2008-09-08
I am a very new user and I had the same problem another forum member suggtested I run ```
sudo displayconfig-gtk
``` in my terminal, then I changed the monitor setting to the one I am using and it let me have a higher res.
Hope this helps

---

