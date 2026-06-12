---
title: "brother 8065dn printer device error after wrong driver installation"
date: 2012-05-10
forum: Hardware
---

### Post by buzzing on 2012-05-10
So my brother printer dcp-8065dn is screwed after i installed dcp-8045dn printer driver. Now all it does is that when i turn it on it goes to self diagnose for 10 minutes and after that it shows Geratefehler in english which means device error. Firstly i installed the two .deb files from the brother website but i didn't know how to install those correctly and i showed the dcp-8045 driver by mistake. Now its not working anymore. i have tried to go to windows 7 and install it but it wouldn't work. Help Please..

---

### Post by plucky on 2012-05-10
> **buzzing said:**
> So my brother printer dcp-8065dn is screwed after i installed dcp-8045dn printer driver. Now all it does is that when i turn it on it goes to self diagnose for 10 minutes and after that it shows Geratefehler in english which means device error. Firstly i installed the two .deb files from the brother website but i didn't know how to install those correctly and i showed the dcp-8045 driver by mistake. Now its not working anymore. i have tried to go to windows 7 and install it but it wouldn't work. Help Please..

Open Synaptic Package Manager and search for DCP-8065DN and it should find brother-cups-wrapper-laser and brother-lpr-drivers-laser. Install them both as they contain the drivers for your printer.

Then connect the printer by USB cable and select the correct driver when prompted to do so.

The printer should now be ready to print.

Good Luck

---

