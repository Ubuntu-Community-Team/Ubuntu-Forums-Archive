---
title: "wireless cardbus causes toshiba laptop hard freeze"
date: 2007-08-29
forum: Hardware &amp; Laptops
---

### Post by fishymark27 on 2007-08-29
Hi,

I have a very old toshiba laptop **Portege 3110CT** It has a PII 300 and 192mb ram.
It is running **Xubuntu 6.10 kernel 2.6.17-12**. When I first started I had the external CD-ROM drive working via PCMCIA. 

 I got hold of an Edimax card with the** RA61 chipset** in it. I'm using the **serial monkey **drivers and the **rt61pci module is blacklisted**. This works when it first goes in, and works ok connected to the internet, as long as I'm not doing anything that requires traffic. As soon as I do some work (but seemingly at not an exact interval) the whole computer stops responding inc. mouse and keyboard input and requires holding down the power button to restart. The computer is very stable even with the card in and set as long as I haven't connected via dhcp. I have tried watching/recording logs, but nothing comes up during the hard freezes. This is very frustrating... I would love wireless AND my cd-rom back


**More background**
Before that I had got a **Belkin BROADCOM **chip wireless card working on the machine after bashing my head against the brick wall for days. However, after a couple of weeks, it progressively got worse and worse at recognising the card, and eventually gave up the ghost. The card still works (I've checked it with a different laptop). The help thread here said do it on a clean install, so then I tried a clean install... Grrr, and it still didn't work in the 3110ct.
I tried updating the **bios** from the **Toshiba** website to **version 7.70**

I'm not sure whether it was before or after the bios update (Which was successful, well it said it was!) but **now my pcmcia cd-rom doesn't work either**. It doesn't even work in the windows 98 partition that I have still got on the HD, but still works on a different laptop. 

The cardbus controller is ToPIC 95 or ToPIC100 depending on which bios update I've used. neither seem to work.

All the lspci, lshw, iwconfig ifconfig etc seem to be fine but I can post them if you think they will help. I'm really looking for something else to diagnose the problem I think though. Oh yeah, and I tried the wirelessTroubleShootingGuide memory allocation changes for the pcmcia config and had no joy. 
Boo Hoo.

Oh yeah.. I don't know whether its a clash with Xfce that's causing the problem, but the applications menu from the taskbar disappeared during one crash. I didn't know that it was possible for a crash to permanantly alter your system, but this doesn't seem very good :(

---

