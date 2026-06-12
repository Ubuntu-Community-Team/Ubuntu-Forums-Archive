---
title: "Zyxel G-110/Power Savings"
date: 2007-08-09
forum: Hardware &amp; Laptops
---

### Post by ddunkin on 2007-08-09
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106987](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106987) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have always been struggling to get consistent use out of my PCMCIA wireless card and things have got worse since moving to Feisty. It is a Zyxel G-110/Prism54 card in an IBM Thinkpad T20. Every once in a while I can get it to load using ndiswrapper drivers and it works fine until I either remove/reinsert it, or reboot. These are similar issues to some of the many bugs currently reported out there, but about 25% of the time it loads and works fine.

I had the exact same issues with this card in Windows XP though. There is an advanced option in Windows for the card (via the normal device manager) that causes issues with this card that I must turn off for it to work, this is setting the 'Power savings mode' to 'disabled'. I cannot find a similar option on the Linux end using pccardctl. Where would I look to disable any possible power savings for the card or the bus?

I have had more reliable results using the prism54 module in Edgy, the newer prism54pci module has not worked once. The card is very similar to a Netgear WG511 from what I can tell.

---

