---
title: "Atheros doesnt work?!"
date: 2008-11-18
forum: Hardware
---

### Post by HuXu on 2008-11-18
So here is a couple outputs to show you what i see...

```
:~$ lspci | grep Ethernet
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
04:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
16:00.0 Ethernet controller: Atheros Communications Inc. Atheros AR5001X+ Wireless Network Adapter (rev 01)
```

the 1st Atheroes card works just find, the 2nd one is my built on card.

Is there a driver that will work with my on board card?

EDIT: I have been doing some research and supposedly the madwifi drivers dont work with Intrepid Ibex's kernel yet, and there is a ath5k driver that might work.  But through this whole process I lost my sound and some of my modules because madwifi wouldnt install, it kept getting errors.  So how do i recover my kernel?  Is it possible to go to a Hardy Heron kernel instead?  I have deleted the Recovery option from my menu.lst so if i need that please post what the entry looks like.

---

