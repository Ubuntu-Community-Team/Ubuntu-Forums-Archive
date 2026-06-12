---
title: "Network Manager and orinoco chipsets"
date: 2006-05-11
forum: Hardware &amp; Laptops
---

### Post by slightly72 on 2006-05-11
Hi,

I have a Intersil Corporation Prism 2.5 Wavelan card, and am trying to use network manager with it (nm-applet). When launching nm-applet, I get the following message:

> The network device "Intersil Corporation Prism 2.5 Wavelan chipset (eth1)" does not support wireless scanning. It will not be completely functional.

The "orinoco_pci" module is loaded for this card. I've tried gtkwifi and got about the same message. nm-applet works fine when I manually supply the network name, but that kinda defeats the purpose of having it.

Is there any trick to have wireless scanning work for this card? I know that wireless scanning works in Windows XP -- so it's not a hardware problem. Would it work if I use ndiswrapper?

Thanks.

---

### Post by cchase on 2007-08-02
I'm sort of a newb myself but I have seen a solution for your problem.  If you use the networking dialog (not network manager) you can add your essid in the /etc/network/interfaces file.  Good luck.

---

