---
title: "Nvidia geforce 6150: Sluggish display"
date: 2014-04-01
forum: Hardware
---

### Post by robbiejormerod on 2014-04-01
I'm having problems with my display, in that windows open and close really slow and navigating around the screen is really lagy. Ive read that changing to a properietary driver can help but I get a choice of four and I want to know which one is the best to use. 
The Graphics port is; Nvidia geforce 6150.
The options for drivers are;
Nividia binary Xorg driver, kernal module and Library from nividia-304-updates (proprietary,tested)
Nividia binary Xorg driver, kernal module and Library from nividia-173-updates (proprietary)
Nividia binary Xorg driver, kernal module and Library from nividia-304-updates (proprietary)
X. Org X server - Nouveau display driver from xserver-xorg-video-nouveau (open source)
The default is the last one.
I tried the first one but the system wouldn't reboot and I ended up having to do a full reinstall of the OS.
As always any input is welcome.:D

---

### Post by SeijiSensei on 2014-04-01
For a card as old as a 6150, I'd probably try the 173 version.

Did you run the "Additional Drivers" application in Ubuntu to install the proprietary driver?  What version did it suggest?

---

### Post by robbiejormerod on 2014-04-13
OK no idea why but switching back to the open source driver seems to have fixed the problem :confused:

---

