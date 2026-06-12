---
title: "linksys WPC54G pcmcia card not working"
date: 2007-05-01
forum: Hardware &amp; Laptops
---

### Post by N0Lif3 on 2007-05-01
I'm running Kubuntu Feisty Fawn on my SOTEC 3000series laptop and am attempting to get a Linksys WPC54G wireless network card working on it.

I've done the steps to get the drivers working through ndiswrapper, but it seems as if the card itself isn't even being detected. When I use the "dmesg" command or look at my network settings, wlan0 is nowhere to be found. The card itself isn't showing any flashing lights.

---

### Post by sdegrace on 2007-05-07
I am having the same problem. I am using Feisty on a Conpaq Presario 2100, trying to get the wireless working from the Live CD - I want to verify that I can get all the crucial hardware working before I do an install. I have version 4.0 of the card, and I obtained the right driver from Linksys. I followed direction like at [http://antonym.org/node/89](http://antonym.org/node/89). ndiswrapper -l shows that the driver is loaded but says nothing about the hardware. pccardctl says the card is there. But wlan0 is nowhere to be found, and there are no wireless networking controls shown in GNOME. Any suggestions are gratefully appreciated - I think my next step is to go backwards to Edgy and see if that works any better, I'll post if that works.

---

### Post by sdegrace on 2007-05-08
OK, I used the wrong driver for v.4 of the card, I needed to use WLIPNDS.INF. wlan0 showed up and I could connect like a charm using the GNOME tools. Right now I can connect to the router, the only problem is that I apparently still can't get out. I'll figure it out and post any results, unless I can't figure it out in which case I'll beg for help again. One clue: network tools says I have an IP6 address, which can't be right I think.

---

### Post by sdegrace on 2007-05-16
Now I have the whole thing solved and I can get WEP! I posted my solution here:

[http://ubuntuforums.org/showthread.php?p=2669349#post2669349]("http://ubuntuforums.org/showthread.php?p=2669349#post2669349")

---

