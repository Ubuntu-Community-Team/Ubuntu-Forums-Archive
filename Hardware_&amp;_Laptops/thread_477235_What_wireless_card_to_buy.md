---
title: "What wireless card to buy?"
date: 2007-06-18
forum: Hardware &amp; Laptops
---

### Post by lean on 2007-06-18
Hi,
I have a laptop where my built in wireless card just broke down.
Any recommendations for a pcmcia or usb wireless card, that works well with ubuntu?

Regards Lean

---

### Post by Crafty Kisses on 2007-06-18
> **lean said:**
> Hi,
I have a laptop where my built in wireless card just broke down.
Any recommendations for a pcmcia or usb wireless card, that works well with ubuntu?

Regards Lean

Hmmm, usually with a lot of the Wireless cards you have to use "NDISWrapper" which is kind of a pain. :(

---

### Post by lean on 2007-06-18
> **Codename said:**
> Hmmm, usually with a lot of the Wireless cards you have to use "NDISWrapper" which is kind of a pain. :(
Yes, it is silly to put money into things without open specification and drivers, when an alternative exist.
But what are the alternative?

---

### Post by Tsen on 2007-06-18
Depends on what you're looking for, but finding a good wireless card can be a pain...
See, what you want is a chipset with good Linux support.  Atheros would be my first pick.  The problem is, the chipset isn't often printed on the physical packaging, or in an online store's description, and in many cases, manufacturers market cards with the same name and model number but different chipsets, so you need to find a card that you KNOW has a linux-supported chipset.  Here's a few, though I don't know if all are still in production:

Airlink AWLC4030
D-Link DWL-650
D-Link DWL-G630 E1 (<-E1 is the hardware revision of the model you want, the others don't have the same chipset.)
D-Link DWL-G650 C3, C4, B5 (<-Again, C3, C4 and B5 are the rev. numbers you want)
MSI CB54G2
Netgear WAG511
Netgear WG511T
Netgear WG511U
Proxim 8470-WD

These all have good Linux support (so you won't need ndiswrapper), and all support packet injection and packet capture, so if you ever want or need to use aircrack or something similar, you're all set.
Also, if you can't find any of those wireless cards, just get on Google product search and put in "Atheros PCMCIA" and you should find a few others that should be linux compatible.

---

### Post by bigken on 2007-06-18
why dont you replace the mini pci card in the laptop ?

---

### Post by beefcurry on 2007-06-18
Just get an Intel Card. those are the most fuss free in Linux.

---

### Post by lean on 2007-06-18
Thanx, I will go looking.

---

### Post by zyzzer on 2007-06-18
> **Tsen said:**
> D-Link DWL-G630 E1 ...These all have good Linux support (so you won't need ndiswrapper)...

I have the G630 and am having the hardest time getting Ubuntu to recognize it.  I got the ndiswrapper because many forums I've read said it makes things a lot easier but when I went to install it Ubuntu told me it couldn't connect to the internet.  I've heard many people get frustrated for "needing internet in order to get wireless internet."  Any suggestions or help is greatly appreciated :)

Zyzzer

---

### Post by ukripper on 2007-06-19
Netgear WAG511 works great in Feisty

---

