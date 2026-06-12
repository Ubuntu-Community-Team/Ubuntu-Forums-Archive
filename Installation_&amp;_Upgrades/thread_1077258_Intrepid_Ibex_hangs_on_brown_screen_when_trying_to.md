---
title: "Intrepid Ibex hangs on brown screen when trying to boot"
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by andeeh on 2009-02-22
Intel S750 1.7Ghz
NVidia GeForce FX5200
512MB RAM
250GB PATA
Wireless LAN

Installation went ok, restarted machine and appears to be going ok, Ubuntu startup screen display, progress bar makes it all the way to the end, screen goes brown and then system hangs.  Keyboard and mouse are both unresponsive.  Will start recovery mode and since I have an nVidia video card I tried editing 
/etc/X11/xorg.conf to change driver to "vesa".

All instructions for doing this that I've come across say that driver should be changed from "nv" but no driver was specified in my conf file??  Tried adding driver = "vesa" anyway, but still hangs.

Any ideas?  Thanks!

---

### Post by Noelyungboy on 2009-02-22
Same Here bro

---

### Post by andeeh on 2009-03-07
Ok, after much experimenting I have concluded that the problem has nothing to do with the NVidia graphics card and is in fact being caused by my Wireless adapter card.  If I remove it Ubuntu will boot no problem, with it inserted the system hangs at the brown screen.  I've had a look around and can only find reports of this happening under Drake and not Ibex and the solution offered there results in Ubuntu completely ignoring the card.  As this is the only way that I can access the internet from that PC that isn't really an option for me.

I don't know where to go next, can anyone help?

Thanks,
Andrew

---

### Post by soltanis on 2009-03-07
What kind of card are you using?

---

### Post by andeeh on 2009-03-07
I had a look using iwconfig and it says it's a Realtek RTL-8185.  I've done a bit more digging and found this guide [http://spikeymikey.net/2008/11/04/belkin-f5d7050/](http://spikeymikey.net/2008/11/04/belkin-f5d7050/) but I can't get ndiswrapper to install at the moment so don't know if it's any use or not.

---

### Post by okamishadow on 2009-03-09
I have the same issue sometimes... So I turn off the PC and start again... fixed... well, also I upgrade from 8.04 to 8.10. After restart I has no mouse and no keyboard... Just works the reset command and the leds. I use the "fix broken pack's" in GRUB options, but the fix is not permanent... Someone and Idea :(

---

