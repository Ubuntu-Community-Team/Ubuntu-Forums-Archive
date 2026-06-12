---
title: "Problem setting up HP Color Laserjet 2600n under Feisty AMD64"
date: 2007-04-29
forum: Hardware &amp; Laptops
---

### Post by Mocker on 2007-04-29
Hi folks,

I just set up Kubuntu Feisty on my Opteron-based computer using the AMD64 version. Now, I'm trying to set up my networked HP Deskjet 2600n printer using the KDE Add Printer wizard. Everything goes fine (detecting the printer, etc.) up until I have to specify the driver for the printer... there seems to be no setting for the "Color Laserjet 2600n" or "Laserjet 2600n" or *anything* with the model number "2600n" in the model list under HP.

Dapper supported this printer just fine, so I was surprised to see that it wasn't appearing in the model column of the Printer Model Selection screen.

I googled for a solution, and found something about this issue in Feisty flight 4 (Bug #88224 [https://bugs.launchpad.net/ubuntu/+source/foo2zjs/+bug/88224)](https://bugs.launchpad.net/ubuntu/+source/foo2zjs/+bug/88224)). However, this doesn't seem to be the issue, since I checked, and I *do* have the "foo2zjs" package installed, so in theory I should have the drivers installed.

Anyone know what's going on, or have a workaround?

Thanks.

---

### Post by Mocker on 2007-04-30
Well, I was manually able to locate the PPD file for the printer, which is actually installed. No idea why it's not showing up in the dialog list. If anyone else is hitting this problem, you need to choose the "Other Printer" button, then browse to:

/usr/share/ppd/foo2zjs/HP-Color_LaserJet_2600n.ppd.gz

---

