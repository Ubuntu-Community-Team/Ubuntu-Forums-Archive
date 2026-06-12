---
title: "How can I diagnose my pcmcia ethernet cards?"
date: 2006-09-09
forum: Hardware &amp; Laptops
---

### Post by Gotou on 2006-09-09
Hi!  I've got 2 old laptops (7+ years).  Each has a different pcmcia ethernet card.  Both cards work in the oldest laptop but only one will work in the newer-old laptop.  I'd like to figure out why.

Here's what I've got:

* Gateway Solo 5300, PIII (newer-old laptop) Ubuntu 6 Linux
* Micron TransPort Trek 2, PII (oldest laptop) Damn Small Linux 3

* Xircom CardBus Ethernet 10/100+Modem 56, RBEM56G-100, CE168X
* NetworkEverywhere Linksys Fast Ethernet 10/100 NP100

The Xircom will work in both laptops, but I can't get ethtool or mii-tool to work with it to see if the card is using full duplex or not.  I suspect not because it is soooo much slower than the other ethernet card on the oldest laptop (Micron).  From what I've googled and searched in UbuntuForums, Xircom is problematic for a lot of folks.

The NetworkEverywhere card works in the Micron just fine.  But it's not even found when in the Gateway.

I've looked through the /etc/pcmcia/config & config.opts files.  Both cards are there.

The oldest laptop (Micron) is running Damn Small Linux.  I've checked it's config & config.opts files.  Pretty much the same as Ubuntu's

So now I'm wondering if the problem is the Gateway laptop itself.  Maybe an IRQ conflict or something.

The Gateway laptop's cd is on the fritz.  It won't load DSL.  I thought I'd see if it was something in the OS or if it was the hardware inside the Gateway.  Fiddling around with making a DSL pen drive to boot the Gateway from.  But there are more urgent projects that need my attention. Frustrating.

What other tools or files should I be investigating?

Buying a new laptop is out of the question for a very long time.

Thanks!

---

