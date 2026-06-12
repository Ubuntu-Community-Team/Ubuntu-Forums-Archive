---
title: "instlux/network config"
date: 2008-10-09
forum: General Help
---

### Post by Robl1974 on 2008-10-09
Hi all, I'm trying to install Ubuntu on an old laptop (C27 toughbook) with no CD or floppy drive and will not boot from USB.  I've downloaded Instlux with edgy 6.06 network, and can get that bit to work, however when it comes to configuring the network it throws it out.

I'm using a net gear DG834G as a router, connected to 3 PC's, (1 linux, 1 XP & 1 fista,) however I don't actually have a network set up - they all independently connect to the internet via the router.  The network card is a PCMCIA card with a realtek  RTL8139 chipset, and the red light comes on to say it's there, but when I use the Shell (ASH) on the installer is just gives     me basic info of 127.0.0.1 as the IP and 255.255.255.255 as the mask, and doesn't see the Netgear router at all.

Now I'm not Mr Linux - I've been running Ubuntu since edgy, but for the last year I've managed to stay away from the terminal window, and my life has been good - can anyone point me in the right direction???? cheers,  Rob.

---

### Post by Robl1974 on 2008-10-09
Right, had a thought over dinner about the IP & Mask - went back into XP and did an ipconfig /all in dos and got the right info: 192.168.0.4 & 255.255.255.0

Now it's letting me select a mirror from a list of countries but it's not allegedly finding any mirrors with 6.06 on - I've checked some of these on the normal PC and they do appear to be there.

That's it, patience has run out deleted it and now trying DSL over UNetbootin to prove the concept, and although the mirror is damn slow it is at least loading it. 

I hope I'm entertaining someone with this.

---

