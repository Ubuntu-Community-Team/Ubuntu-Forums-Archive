---
title: "how to ignore orinoco modules to use hostap ?"
date: 2006-04-06
forum: Hardware &amp; Laptops
---

### Post by s3phiroth on 2006-04-06
Hi there.

I'm running Dapper Drake and i have a Senao NL-2511CD PLUS EXT2 wireless card, powered by an Intersil Prism 2.5 chipset.

I know that i can use other drivers with this card, but i want to use the hostap drivers, given it's capabilities. However, everytime i plug the card in, i get the orinoco modules loaded. I have them being ignored on /etc/hotplug/blacklist.d and /etc/modules but they still get loaded everytime i plug in the card. I already searched a lot, read a lot of forum posts about this subject and i couldn't got to any conclusion. The closest i could get was in this thread [http://ubuntuforums.org/showthread.php?t=131158](http://ubuntuforums.org/showthread.php?t=131158) where in the second reply the guy says:
"If you have a pcmcia card (not a cardbus card - they look similar) or are using ndiswrapper as a driver, my example will not suppress loading your existing drivers. Those cards are loaded by different configuration files."

So i'm kinda lost here. I removed pcmcia-cs, because i sometimes got the message that this kernel was using pcmciautils instead, and i tought that maybe i was getting some interference from pcmcia-cs config files, so i purged it.

This is what i get from lshw:
*-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:6f:05:4b:6b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15rc3 firmware=Intersil 1.4.9 link=no multicast=yes wireless=IEEE 802.11b

If there's any more info i can provide, please tell me.
Thanks in advance.

---

### Post by Jason_25 on 2006-04-06
For some reason the blacklist does not work on dapper.  You have to go into /lib/modules and manually remove the driver.

---

### Post by graham on 2006-04-08
That's odd, the blacklist seems to be working fine for me.

---

### Post by s3phiroth on 2006-04-08
Geez ! I was starting to go mad. I'll try that then. However i won't have a chance to try and connect to an access point during the next week because i don't have one.

---

