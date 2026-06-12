---
title: "Network Card Schizophrenia"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by TSellers on 2009-01-21
My system has two network cards, one for the WAN, and one for the LAN.

The onboard card is attached to the LAN normally and works all the time.

The other PCI card returned a hardware error, so as I have about 7 cards laying around, I tried a few of them. It seemed that if I placed one in a new PCI slot, I would then get WAN access through it until I rebooted, then lose it again. If I switch the cable up to the imbeddded controller, then I would have access.

So it seems like Ubuntu is becoming confused as to which card to use and I assume I have to tell it to use the 2 cards.

Could anyone set me in the right driection as to how to go about doing that?

---

### Post by Pumalite on 2009-01-21
Get a router and place it between your Winmodem and an Ethernet. Make it give you DHCP and a dynamic IP

---

### Post by TSellers on 2009-01-21
Still having this problem.

Thanks. Already did that. The WAN cable goes to a router which assigns it a local IP. The LAN Cable goes to an ethernet switch. This switch is isolated from the network the router is on, and there is no internet connectivity on this network. It does not need TCP/IP.

The problem appears to be the system assigns TCP/IP to the embedded card by default. I need to be able to tell the system that one card uses IXP and the other uses TCP/IP for example. I need to set the ssytem up so I can tell it to assign TCP/IP to one card, and LAN protocols to the other.

---

