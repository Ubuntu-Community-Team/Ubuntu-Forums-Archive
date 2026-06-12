---
title: "Two different sound devices"
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by AstronomyDomine on 2007-03-08
I just installed Feisty Herd 5, and everything was working beautiful, even the sound was working, until after one reboot, the sound just wouldn't play. I looked at Kmix and noticed that the default mixer was VIA 8237. Now my computer has a VIA chipset, but I have the onboard sound disabled because I have a Creative Audigy sound card. It seems to let me change the mixer to my Audigy (SB0350), but that does absolutely nothing to make my sound work. 

Any ideas?

I'm using Kubuntu Feisty Herd 5 with all of the latest updates.

---

### Post by AstronomyDomine on 2007-03-09
Any ideas? Anybody? Please?

---

### Post by bettermentflux on 2007-03-12
Not a solution, but I do feel your pain; I have an Audigy card in my laptop that I cant utilize under Feisty either. The internal card does work fine, but although Feisty recognizes the Audigy when plugged in, Selecting the Audigy in the Sound Device Preferences dialog does nothing.

If anyone has their Audigy working under Fesity, please let us know how.

---

### Post by DoorGunner on 2007-03-13
Hi .... I found a solution that works

I have the same via8237 and audigy problems you and may people have had.

What i think is happening is Via and audigy are both competing for the job of sound controller. This has continued even though i turned my onboard sound off at the bios level.  The kernel still seems to recognizes that it is there. This is not good and seems to be the root of our troubles. You have noticed this too in your kmixer with both via and audigy being available. Even sometimes audigy not even being available.

This is what I did to solve the problem

> sudo gedit /etc/modprobe.d/blacklist

add the following lines to the bottom of the file

#added to correct sound issues
blacklist snd-via82xx


What this does is prevent via82xx from ever being loaded into the modules on start..... ever. So someday if you take the audigy card out and want to use your via onboard sound you will just have to go back in and remove the lines.

After having done this you will note the next time you reboot you will only have audigy controlling kmix not via82xx. I have run this configuration for a while now and havnt had sound problems since.

---

