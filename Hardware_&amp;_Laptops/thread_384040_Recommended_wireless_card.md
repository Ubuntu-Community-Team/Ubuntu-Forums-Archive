---
title: "Recommended wireless card?"
date: 2007-03-14
forum: Hardware &amp; Laptops
---

### Post by Toadmund on 2007-03-14
A friend at work has broken windows, so I told him I can get him on the net with a free OS (Ubuntu of course)
He has not yet bought a wireless card.

What is recommended?
The ISP will be aliant telecom.

---

### Post by bukwirm on 2007-03-14
Take a look at [this page]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/") for some information about wireless and linux.

I have an Intel PRO/Wireless 2200BG card, and it works fine.

---

### Post by Toadmund on 2007-03-14
Well, I wrote down your card info, if it works for you, it's good enough! There are so many models of wireless cards on that site, I suppose I should see what brands are available first.
Thanks:)

---

### Post by kambei on 2007-03-15
I use a D-Link DWL-G650 (Atheros chipset -- hw ver. b5 / fw ver. 2.54) PCMCIA card with my laptop... once you grab the necessary modules:

sudo aptitude install linux-restricted-modules-generic

...the card is detected, easily configured, and works well.

When buying a wifi card for linux compatibility, take careful note of hardware version #... Wifi manufacturers are notorious for changing the chipset on cards without changing the model #... possibly changing a 'supported' card to 'unsupported'...

---

### Post by ctt1wbw on 2007-03-15
Wow, that's the same card that I just bought yesterday for my Thinkpad T30.  I'm using Fedora Core 6 on this laptop, and hopefully I can get it to work.

I guess you have to install ndiswrapper no matter what distro you use?

---

### Post by kambei on 2007-03-15
> **ctt1wbw said:**
> Wow, that's the same card that I just bought yesterday for my Thinkpad T30.  I'm using Fedora Core 6 on this laptop, and hopefully I can get it to work.

I guess you have to install ndiswrapper no matter what distro you use?

You're in luck... ndiswrapper is not required... there are madwifi sources available to build a (proprietary-licensed) kernel module - ath_pci - that supports this card. On Debian Etch I was able to compile and use the module successfully... on Ubuntu, the modules are already provided in the 'linux-restricted-modules-generic' package.

I am using the wifi right now on my Thinkpad T23... :-)

---

### Post by Toadmund on 2007-03-15
OK, thanks, I am going to get this stuff down, and see if these models are in the stores, thanks.

Anyone else?

PS, unknown cpu or motherboard, and it is a desktop computer (if that makes any difference)

---

### Post by Toadmund on 2007-03-16
'bump'
I would like to give my friend more brands to choose from for wireless cards, I want to know who uses what brand that works best for Ubuntu.
How was your experience?

---

### Post by RussellWing on 2008-04-26
I was using an ASUS PCI wifi card based on a Broadcom BCM4318 which has consistently caused problems with Ubuntu for the last 3 upgrades.

Just bought an EDIMAX PCI wifi card based on the Ralink chipset. These guys Open Source their drivers and they work out of the box with Hardy Heron, and most other distributions for that matter. These cards have a nice antenna with a separate cable that can be located away from the case to get a good signal.

The exact Chipset reported by lspci is "RaLink RT2561/RT61 802.11g PCI"

Check out for more details:

[http://www.linuxemporium.co.uk/products/wireless/](http://www.linuxemporium.co.uk/products/wireless/)

I recommend you support manufacturers that get Open Source and reward them by purchasing their products in preference.

Cheers,
Russ.

---

