---
title: "nvidia drivers on Inspiron 8200"
date: 2009-10-19
forum: Hardware
---

### Post by bugmo on 2009-10-19
I installed ubuntu 9.04 on my Dell Inspiron 8200 laptop (1.7 GHz, 1GB RAM, NVIDIA GeForce4Go/16 MB).  Out of the box it seems reasonably responsive, however I have been unable to successfully install NVIDIA drivers, either from the Jaunty repositories or from NVIDIA directly.  In both cases upon rebooting the response is very slow, unusable really.  What am I doing wrong?

---

### Post by Dark_Stang on 2009-10-19
You should just be able to go System > Administration > Hardware Drivers and check what you need to install...

Open up a terminal and run glxgears. If the gears run smoothly then hardware acceleration is working.

---

### Post by bugmo on 2009-10-20
I just did this again on a fresh install.  At first I get a completely blank screen.  I read somewhere that you have to insert Option "UseDisplayDevice" "DFP" in the Screen section of xorg.conf.  After doing this and rebooting again, graphics rendering is very slow.  You can see the menus draw (it's that slow).

I looked at the "Appearance" preference and Visual Effects was set to "Normal".  Before installing the driver it was set to "None".   I reset it to "None" and rendering is now acceptable again, and glxgears appears normal.

Of course one of the reasons I want the Nvidia driver is for visual effects...

---

### Post by bugmo on 2009-10-21
I figured this out.  When I started up the computer, the BIOS showed 16 MB of VRAM on the video card.  Looking up the service tag for this computer at Dell, the system configuration is 32 MB, and in fact there does not seem to be a 16 MB card even available.  I took out the video card and reseated it, and on restart: voila!  32 MB!  Much better performance now...

---

