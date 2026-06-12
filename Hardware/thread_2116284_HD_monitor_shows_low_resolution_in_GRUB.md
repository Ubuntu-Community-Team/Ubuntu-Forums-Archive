---
title: "HD monitor shows low resolution in GRUB"
date: 2013-02-15
forum: Hardware
---

### Post by zeiz on 2013-02-15
Ubuntu 12.04 64bit.
Just changed my old 22" 1680x1050 Samsung to HD 23.6" 1920x1080 Asus.
Everything looks very beautiful except grub splash screen.
It was high quality full screen (1680x1050) on my old monitor but it's limited now to 1280x800(720) on the HD one. 
*vbeinfo* shows it as maximum resolution while the video chip (GForce8200) is capable for 1920x1200 by *hwindo*.
I also noticed that before OS starts the screen is always small regardless grub splash image presence.
It's interesting that the old monitor serving now ancient box with ATI x700 card still shows full screen quality grub splash.

So all the hardware and software has no changes except the monitor.
What could be wrong?

---

### Post by Mark Phelps on 2013-02-15
Install Grub-Customizer.  It will provide menus through which you can easily set the resolution of the GRUB boot screen.

---

### Post by zeiz on 2013-02-15
Thank you, I'll give it a try.

However my goal is not just to get rid of the small inconvenience but rather understand why modern HD monitor in vesa mod cannot perform as good as old, budget class one?
Any ideas?

PS. When X is running the HD monitor for sure outperforms the old one.

---

### Post by zeiz on 2013-02-15
Tried [this]("http://byobu.info/wiki/Changing_Plymouth_Resolution_in_Ubuntu") - doesn't work for me. 
Still don't understand what's wrong with my monitor.
Any other ideas?

PS. Grub-customizer didn't help too. Instead it led to severe problems and I had to reinstall grub2. 
I believe the issue is not software but monitor itself.

---

