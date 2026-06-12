---
title: "Why would you recommend your graphics card?"
date: 2011-10-29
forum: Hardware
---

### Post by Neill_R on 2011-10-29
Hi

looking for a recommended graphics card. 

I have a Packard Bell I-Media 1238/1 PC 2GB Ram this has SIS motherboard graphics.

neill@charles1:~$ sudo lspci |grep VGA
00:09.0 VGA compatible controller: S3 Inc. 86c968 [Vision 968 VRAM] rev 0
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter
neill@charles1:~$ 

Monitors  SIS DELL 17 
                S3   HP S2231a (VGA / DVI )

In this mode (BIOS AGP/PCI set to PCI ) I have dual screen Windows XP PRO system.

UBUNTU

The S3 becomes the active device once the card is installed. Under UBUNTU 11.04 i can only run the recovery console in low resolution mode. I would like to be able to sort it out but it is just to complicated and confusing so I am opting to purchase a VGA / DVI PCI card that will work straight away. A near perfect installation.   What is your recommendation and why?

Thank you in advance

Neill

---

### Post by tartalo on 2011-10-29
I'm happy with a Nvidia Geforce. In Ubuntu it has two drivers available: Nouveau, which is free software, has good enough performance for not very demanding 3D apps and keeps getting better, and also the Nvidia binary driver which is not free but performs better for games and is really easy to install.

---

### Post by Neill_R on 2011-10-29
The GE 430 being the cheapest is an AGP slot card what i require is a PCI card since if I use the AGP slot I can not use the motherboard graphics. Unless someone knows a way that i do not?

---

### Post by tartalo on 2011-10-29
There are PCI cards by other brands that use the Nvidia chip, like this:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=854467&CatId=319](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=854467&CatId=319)

There might be better or cheaper options, I didn't do a research.

---

### Post by tartalo on 2011-10-29
I've reread your needs. I did NOT try dual monitors using the onboard card, maybe someone else can give you better advise, sorry.

---

### Post by Neill_R on 2011-10-29
I think my options are this

1 use motherboard graphics and get a better PCI VGA card or
2 Use an AGP card that can do VGA and DVI 

   Not sure what the functionality of such a card would be called but i want it to do extended desktop in windows and in UBUNTU

---

### Post by oldfred on 2011-10-29
You need to be careful on power supplies. If you put in too new a video card it will require lots of power and an older vendor system usually just has a power supply for the system as configured to hold down cost.

Lots of info on video cards.
[http://www.tomshardware.com/reviews/best-graphics-card-gaming-performance,3042.html](http://www.tomshardware.com/reviews/best-graphics-card-gaming-performance,3042.html)

---

