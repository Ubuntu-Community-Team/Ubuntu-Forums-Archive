---
title: "my netgear wg511 card"
date: 2007-11-11
forum: Hardware &amp; Laptops
---

### Post by kinghippy on 2007-11-11
Hey, I've tried to follow all the instructions that have been given to other users, but I guess I'm not doing something right. My computer thinks it is recognizing my netgear card. When I type sudo lspci -v in the terminal, I get this:

02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w835 [Libertas] 802.11b/g Wireless (rev 03)
   Subsystem: Netgear WG511v2 54 Mbps Wireless PC Card
   Flags: 66MHz, medium devsel, IRQ 9
   Memory at 24000000 (32-bit, non-prefetchable) [disabled] [size=64K]
   Memory at 24010000 (32-bit, non-prefetchable) [disabled] [size=64K)
   Capabilities: [40] Power Management version 2


So it seems that I should have connectivity, right? Only when I type the ndiswrapper -l command I get this:

2802w : invalid driver!


I have blacklisted the prism54 module. There are no lights blinking on my wireless card, and it simply doesn't respond when I am in a situation where wireless is available. Can anyone help me?

I am running 7.10 xubuntu on my sony vaio laptop. Thanks

---

### Post by kinghippy on 2007-11-11
bump

---

### Post by John Jason Jordan on 2007-12-22
> **kinghippy said:**
> bump
I finally succeeded. I posted the details here:

[http://ubuntuforums.org/showthread.php?p=3999047#post3999047](http://ubuntuforums.org/showthread.php?p=3999047#post3999047)

That thread has a link to drivers that work better.

---

