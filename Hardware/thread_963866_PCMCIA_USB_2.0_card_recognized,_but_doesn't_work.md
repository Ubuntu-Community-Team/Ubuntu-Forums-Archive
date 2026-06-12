---
title: "PCMCIA USB 2.0 card recognized, but doesn't work"
date: 2008-10-30
forum: Hardware
---

### Post by beengone on 2008-10-30
I have an HP Omnibook 900b on which I just installed and updated the latest (as of today) Xubuntu 8. Thankfully, all my hardware that did not work under 6 is now working.  But, I added a USB PCMCIA card (Zonet ZUN2200) and the machine sees it but it does not power or recognize a mouse/flash drive/etc.  My PCMCIA Ethernet card works perfectly.  Here is the stuff that looks useful from lspci:

02:00.0 Ethernet controller: Abocom Systems Inc ADMtek Centaur-C rev 17 [D-Link DFE-680TX] CardBus Fast Ethernet Adapter (rev 11)
06:00.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
06:00.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
06:00.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)

Any idea why this won't work and how I get it to work?

---

### Post by waspinator on 2009-11-29
Same problem in 9.10 (Server). Trying to use this card in an old laptop that will serve as a file server with external USB 2.0 drive. Is there a PCMCIA USB 2.0 Card that works 100%?

Got this one on ebay ... should have checked compatibility first I guess, but Ubuntu has been so good about hardware compatibility I got lazy ...
[IMG]http://imgs.inkfrog.com/pix/kitsparts/pcmcia03_1.JPG[/IMG]

---

