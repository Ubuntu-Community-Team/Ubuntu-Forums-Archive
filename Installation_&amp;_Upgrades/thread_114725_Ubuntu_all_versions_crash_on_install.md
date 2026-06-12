---
title: "Ubuntu all versions crash on install"
date: 2006-01-09
forum: Installation &amp; Upgrades
---

### Post by Fregster on 2006-01-09
Well after months of testing Ubuntu I decided to use it as my main OS.

And it don't work, bummer.

Okay I started with 5.10 and during the installation of the packages it frezzes around 70% (Gstreamer I think)

I think maybe the CD is nackered so I install 5.04 with the plan to upgrade. It installs but after login the screen garbles and crashes - great (now think this maybe because of the 7800 GT). I try the recovery console and install the nvidia-glx and enable. The screen is really dark and hangs during login.

maybe 5.04 does not support the A64 or GF7800 lets download and try 5.10 x64.

Same as 5.10.

I managed to reboot in to recoverey mode and try apt --configure -a

It goes through and installs all the other pkg's

Login manager now loads. After a second or two it jumps back to the installer to "Register Documentation" well after 8 hours I guess thats crashed too.

back to the terminal and enable the nvidia-glx. Same as above.

Tryed Drapper same as 5.10, Gona try it with a PCI s3 Verge latter see if that works.

Anyone have any helpfull ideas?

---

### Post by Sef on 2006-01-09
Have you tried the Live CD and see what happens?

---

### Post by tbresson on 2006-01-09
Perhaps you could try and live CD?

And/or maybe the Kubuntu version instead of Ubuntu - just to see if there's an issue with Gnome?

I've experienced some weird stuff to on my AMD 1900+ with GF3. Live CD 5.04 worked, Kubuntu 5.04 worked - Ubuntu 5.04 just didn't.

I changed my motherboard, my CPU (to P4) and of course the RAM and now it runs just great. Can't really tell what the reason was since I changed a lot of things.

---

### Post by Fregster on 2006-01-09
Could not find my Live CD last night, might try it latter.

I am thinking that...

If I try an install with the PCI card see if that works.

Install the nvidia-glx reboot, shutdown. Put in my PCIe card. Restart, is this the correct way with Linux?

If I can just get it to install properly, does anyone know if you can run the Register Documentation from the terminal, maybe I can get an error code before re-install.

Any information (I can't seem to find any) about Ubuntu and Geforce 7 series?

---

