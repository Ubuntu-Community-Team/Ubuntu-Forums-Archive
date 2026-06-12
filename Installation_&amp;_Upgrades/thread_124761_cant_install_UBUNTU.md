---
title: "cant install UBUNTU"
date: 2006-02-02
forum: Installation &amp; Upgrades
---

### Post by jumiclads on 2006-02-02
DVD in drive, restart laptop (HP Z8290) type Install, press enter, starts installing first two processes but extremely slow, like 20 mins to do first line of dots, then gets eventualy to choose language etc, I answer all questions and stats detectig hardware etc. It then tells me something is wrong with graphics card and cannot continue. Any Ideas?

---

### Post by CompShrink on 2006-02-02
Um, well first off, what's your video card?

---

### Post by jumiclads on 2006-02-02
My Graphics card is an ATI Mobilty Radeon X600

---

### Post by jinxpk on 2006-02-02
i have the same problem with a radeon x600. i tried what someone suggested configuring settings using "sudo dpkg-reconfigure xserver-xorg" but it didn't help. I still get an error that says the graphics card isn't set up correctly. Does anyone know how to fix this problem? i'm very new at this so any help would be appreciated. thank you!

---

### Post by CompShrink on 2006-02-07
Two options, first one is better:

**1. low-end basic graphical install**
Try typing:   linux vga=771    at the command line prompt that pops up before the installation starts. That will install ubuntu with very basic graphical support, no 3d accel or anythign fancy, no hi res either, i believe.

It will still try to use the ati driver, which will fail. But it should install and give you a command prompt, from there open up your xorg.conf file, and set the driver from "ati" to "vesa" in your xorg.conf file. Reboot and it should work.

Once you have a gui, should be easier for you to figure out how to get better drivers working (or wait for a new version, if need be?)


**2. no graphical at all install**
Try typing:  server   at the command line prompt that pops up before the installation starts. That will install ubuntu without graphical support, as in command line only.

If that works, you can try to get the installation of the gui working, and it's a starting point. If that doesn't even work... we've got a big issue. 


Tell me if either of those work.

---

