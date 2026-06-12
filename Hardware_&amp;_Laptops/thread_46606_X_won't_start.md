---
title: "X won't start"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by MattiasS on 2005-07-05
Hey!

I'm new to this particular dist of Linux and very curious of the Linux world since I haven't been using Linux for very long.

The problem I have though is that after I installed the OS I coulnt start up X that good :P
Chose the resolution 1280x1024 when I was prompted to chose a resolution and went on. When the logintext came (textmode) and it tryed to start X it just came a output that sayed "No device found", thought it was weird since I checked xorg.conf and my graphiccard was there. My monitor was generic though but it shoulnt matter right?

Cant post the contents of xorg.conf here yet but I can do it once I reboot and print the page :P (no network access in Ubuntu yet)

Hope you can help me!

---

### Post by varunus on 2005-07-05
Could you post your xorg.conf and your /var/log/Xorg.0.log here?  The log file will say why X is failing to load.

---

### Post by MattiasS on 2005-07-06
Changed the driver to vesa now. That worked but the refreshrate is still weird though. (cant run 1280x1024@100hz). 
I have no network in Ubuntu yet, once I get that I can post my logfiles. Need an compiler who likes my Ethernet adapter first :P

---

