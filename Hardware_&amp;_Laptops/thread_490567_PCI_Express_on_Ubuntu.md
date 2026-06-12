---
title: "PCI Express on Ubuntu"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by 6591Dog on 2007-07-02
I have an ECS RS400-A motherboard with an on-board ATI RADEON XPRESS200 chipset.  I installed an ATI RADEON X300 PCI Express graphics card and disabled the on-board video.  It ran well under windows and worked well during the installation of Ubuntu.  When I performed the reboot at the end of the Ubuntu installation the boot-up tried to use the on board video card and eventually disabled the xserver, took me to a command line etc...  I tried to get it to detect my PCIExpress card in the PCIExpress slot but it never would.  I removed my PCIExpress card, enable the onboard video and "voila"  Ubuntu was up and running.  Is there something I need to do in order to tell Ubuntu to look at my PCIExpress slot and direct video there?

---

