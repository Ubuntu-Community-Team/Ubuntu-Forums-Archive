---
title: "Configuring laptop to toggle on/off external monitor"
date: 2008-08-20
forum: Hardware
---

### Post by csa3d on 2008-08-20
Hello,

I've got a laptop with an attached external LCD.  I am running an nvidia card, and have it currently attached and working in TwinView mode.

What I haven't been able to find the answer on the forums about, is how do I go about configuring ubuntu to allow me to toggle display profiles, as in windows, so that when I want to "undock" from my desktop and go mobile, xorg will turn off twinview and display ONLY on the laptop, without displaying a virtual screen off to the side as though my external monitor is still attached.

Any help on this matter would be killer!

-csa

---

### Post by Daelyn on 2008-08-20
> **csa3d said:**
> Hello,

I've got a laptop with an attached external LCD.  I am running an nvidia card, and have it currently attached and working in TwinView mode.

What I haven't been able to find the answer on the forums about, is how do I go about configuring ubuntu to allow me to toggle display profiles, as in windows, so that when I want to "undock" from my desktop and go mobile, xorg will turn off twinview and display ONLY on the laptop, without displaying a virtual screen off to the side as though my external monitor is still attached.

Any help on this matter would be killer!

-csa

You will have to write a script that cycles between modes somehow, but, it is probably a pain. I'm quite sure that changing nvidia graphical properties requires a restart of X (your graphical interface) which means it will be a pain however you do it.

I would suggest you go into [http://forums.nvidia.com](http://forums.nvidia.com) and look in their linux forum for any scripts or information regarding this. It is a "generic linux" query, so, they would be the source.

---

### Post by pwnprog on 2008-08-20
i unfortunately don't think that it will be as simple as unplugging and away you go. 

if you don't mind spending an extra 20 seconds, the way i usually do this is to go into nvidia settings, select your laptop screen and make it a separate x-screen. then select your external display and disable it. 

then you save everything to x-configuration, log off, and that should do the trick.

i've never bothered to write any scripts for it, cause once you figure out how to do it manually its pretty easy.

---

