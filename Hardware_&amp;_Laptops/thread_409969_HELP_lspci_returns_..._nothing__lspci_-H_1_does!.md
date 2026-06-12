---
title: "HELP: lspci returns ... nothing  lspci -H 1 does?!"
date: 2007-04-15
forum: Hardware &amp; Laptops
---

### Post by KillerKiwi on 2007-04-15
Help running lspci retunrs nothing... but if I run "lspci -H 1" the devices are all visible... anybody know how to make the devices load correctly( theres an ethernet, usb controller, vga controller etc and a few other things)? 

The vga controller works.. I can start X but the USB, ethernet etc dosnt seem to want to load..

Any help greatly appreciated

---

### Post by KillerKiwi on 2007-04-15
To answer my own question :)

Add pci=noaspci to the grub boot line

---

