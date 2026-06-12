---
title: "Can not get driver for PCI graphics to stay enabled."
date: 2009-01-15
forum: Hardware
---

### Post by user11 on 2009-01-15
I have an EVGA 256-P1-N399-LX GeForce 6200 256MB 64-bit GDDR2 PCI Video Card that seems to keep getting rejected by Xubuntu/Ubuntu (both 8.10 and 8.04). It's installed in an older pre-fab system, currently a compaq presario 5030 with a pre-2000 bios. I rebuilt a power supply to give the recommended minimum watts.

The OS sees that card and recommends a driver, but after I install the nvidia driver and reboot, the system goes into low graphics mode. I tried this card in a few other computers as well...same issue.

I was however able to get this set up (and others) working by installing wNop v0.2-a puppy linux derivative, and Winows XP. The only difference between the two is that Youtube is smoother in windows.

I'm suspecting that there is a config file somewhere that searches for the graphics device in AGP or PCI-e only? Does anyone have any suggestions as to how to get the nvidia drivers working in Xubuntu/Ubuntu?:confused

---

### Post by user11 on 2009-01-18
anybody...

---

### Post by user11 on 2009-01-24
Tried blacklisting agpgart, still no luck.

---

### Post by user11 on 2009-02-11
Epic win for Microsoft.

---

