---
title: "Quick question about wifi"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by Rapidsnow on 2007-09-12
Well hopefully quick, I am not so sure anymore.

So I have an HP dv6258se with dual core turion 64x2 processor. The wireless card is the Broadcom Dell Mini PCI WLAN 1390 (Or some combination of the phrase.) I have a dual boot system with glorious ubuntu for almost everything and stinky windows for music only.

My wireless card had been working fine after getting ndiswrapper to install the drivers for ubuntu, but it suddenly stopped working on both Ubuntu and windows. I called hp support and they had me reinstall drivers, update BIOS, and after 2.5 hours of listening to an Indian accent, they sent me a new wireless card. 

Alright, now I have said card and I have installed it, still not working. I have tried 
```
lspci -v 
```and 
```
iwlist scanning
```. Neither of those show up with my broadcom dell card. So my next thought is that I might have accidentally blacklisted the card (although I have no idea how) or something happened in its recognition, so I am hunting for where to find the PCI devices and how to tell what is going on. 

I am pretty good at following instructions but I am also a noob to some degree. I am hoping it is not something physical in the wiring so my last effort is to appeal to the wonderful community of computer/ubuntu nerds we have here (hey I am one too, its not an insult) to try to help me. Thanks for reading this long plea and I hope you can help.

---

### Post by Rapidsnow on 2007-09-13
Bump... I really need any advice, even if it is just where to look for the device.

---

