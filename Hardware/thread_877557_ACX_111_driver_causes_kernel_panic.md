---
title: "ACX 111 driver causes kernel panic"
date: 2008-08-01
forum: Hardware
---

### Post by NogginBoink on 2008-08-01
Greetings, I'm a new Ubuntu user from the land of Windows and could use some newbie help, please.

I'm having trouble using my AirLink (yay quality!) b/g PCMCIA card under Ubuntu 8.04 desktop.  Ubuntu says this is a "Texas Instruments ACX 111 54 Mbps Wireless interface."

When I have the card inserted at boot time, Ubuntu detects the card and detects the SSID's of wireless networks around me. However, when I connect to my access point (using a 64bit hex WEP key), my machine does a kernel panic a few seconds later.  (At least, I assume that's what the flashing capslock LED means.)

I'd like to know how to troubleshoot and solve this problem.  I'd happily gather more data if someone could instruct me what's needed.  The laptop works find with the hardwired Ethernet port.

Thanks,

-Noggin

---

### Post by reidkaufmann on 2008-09-19
I also see a crash when I login with the acx111 driver (used for my pci Netgear adapter wg311 v2).

---

### Post by tosszyx on 2008-12-10
Hi

I'm affected also with this [ _bug_ ]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/279287"). So far what you can do is to blacklist the acx driver and use the ndiswrapper to use the windows binary drivers.

You can use the instructions given [_here_]("http://ubuntuforums.org/showthread.php?t=434983")

Good luck !

---

