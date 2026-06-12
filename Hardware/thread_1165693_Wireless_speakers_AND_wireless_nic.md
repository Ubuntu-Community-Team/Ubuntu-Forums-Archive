---
title: "Wireless speakers AND wireless nic"
date: 2009-05-20
forum: Hardware
---

### Post by serapis5 on 2009-05-20
Hello all.

I've tried searching the forums for an issue similar to this, but really haven't come up with anything close enough.  I have a Linksys Wireless G pci card in the box I keep for media purposes (BCM4306 802.11b/g).  Also a linksys wireless G router model in G-only mode (WRT54GS).  Because this machine is in the living room and connected to my home theater system, I am running into a conflict with the wireless speakers also attached to the home theater.  They knock out the network connection between the router and the Ubuntu box.  Model on the speakers is Panasonic SA-HT640 which utilizes wireless B.  Ordinarily this is not a big issue, but if I need the network access at the same time that music is streaming I'm out of luck.

I've tried different channels with the router, all three modes for the router (B only, G only and Mixed) and just about everything else I could think of.  There was some improvement with the upgrade to Jaunty in that the network connection now is in and out, but very very low when connected.  If anyone has any grand ideas, I would really appreciate a hand on this one.

Thanks

~~~~~~~~~~

So here it is 20 minutes after posting and I figured it out.  Figures, I've been beating this up for two release cycles, lol.  Turns out the data rate from the router was set to still be compatible with wireless B even though the router was in G-only mode.  Change Basic Rate back to Default on the advanced wireless tab in the router and now no conflict.

Feeling sheepish, but hope this helps someone else.

---

