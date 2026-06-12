---
title: "Curious Networking"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by rmcgibbo on 2007-06-14
Trying to get wireless up on my new and fun copy of Feisty. This is my first experience with linux.

I have a Linksys WMP11 v1 PCI Wireless card with a prism 2.5 chipset.
"01:0a.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)" is the relevant readout from lspci.

The wireless card wasn't being recognized at all, though its drivers are supposed to be included on the kernel, but i found this[http://ubuntuforums.org/showthread.php?t=455559]("http://ubuntuforums.org/showthread.php?t=455559")
and followed the instructions (i blacklisted "prism2_pci" in modprobe.d.

All of a sudden, i start seeing wireless networks everywhere. My card goes from having a wire icon in network manager to a wireless one, and the networks around me are popping up.

My network however, doesn't seem to come up. I'm sitting right next to the access point, a Netgear Pre-N router that is brand spanking new.

In WinXP i can connect to my network and get on the internet through it, and get quote unquote excellent signal strength. However, in the network-manager, i can't really connect to it. When it does show up on the list of available wireless networks, i can't join it. When i click on it and it spends about 30 seconds attempting to join the network, it ends up not joining my network, but an unsecured one next door. (I've been running my network unsecured so far as well, i thought that presented less potential complications).

So i can sometimes see my network but not connect to it, while i can perfectly connect to the network next door. In WinXP however, i can connect to both.

What's the deal?

---

### Post by CrazyGuy123 on 2007-06-14
You say "sitting right next to" - there are a few bits of wireless hardware out there that don't work too close, so try about 10m away.

Try fiddling with the advanced wireless settings in the router.  To start with make sure security is off (no WEP, no WPA etc.), and make sure broadcast SSID is ON.  If there's a beacon interval setting, make sure thats set fairly frequently, like every 100ms or so.

It may help to change the SSID as well, in case the ubuntu machine has cached some details about how to connect (eg. network keys), which have now changed.

---

