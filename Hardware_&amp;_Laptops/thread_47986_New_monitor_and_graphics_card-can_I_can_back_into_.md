---
title: "New monitor and graphics card-can I can back into ubuntu?"
date: 2005-07-10
forum: Hardware &amp; Laptops
---

### Post by bailout on 2005-07-10
I have just installed a new monitor (tft instead of crt) and a new graphics card (9800pro instead of gf4200). I multi boot with 3x winXP and one Ubuntu. I didn't do any preperation to my Ubuntu install before adding the new hardware so it still thinks it has an nvidia card running a crt instead of ati running tft as it now is.

Is it possible to rescue my ubuntu or should I just reinstall? I know I will have to get rid of the nvidia drivers and get it to change the monitor id to run correct settings for a tft. I installed the nvidia 3d drivers from Ubuntu by the way. I have a live disk so wondered if it ispoassible to use this and edit the files on my install.

I am still a noob so haven't a clue how to do this and hence am leaning towards the reinstall method.

thanks

---

### Post by Leif on 2005-07-10
You could try to login with the safe mode, and then run sudo dpkg-reconfigure xserver-xorg

---

### Post by bailout on 2005-07-10
Now for a total noob question. Does selecting "recovery mode" in grub boot into safe mode? And will this not run the nvidia drivers and the monitor settings for my crt. I don't want my new monitor or card to blow up.

---

