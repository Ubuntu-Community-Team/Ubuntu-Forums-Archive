---
title: "(Repost, with better title) ess 1878 sound card hardware conflict with linksys WPC11"
date: 2007-02-12
forum: Hardware &amp; Laptops
---

### Post by diablo75 on 2007-02-12
I recently got my ess 1878 sound card working in a Compaq Armada 7800 following the directions posted [_here_]("http://ubuntuforums.org/showthread.php?t=12525&page=2") by Nedder.

Something that's happened with this laptop is that when the wireless networking card (A Linksys WPC11 v.4) is being used, it generates a fast crunching noise through the speakers, although it's a bit faint and not all that annoying. But when the laptop attempts to play sound at the same time, the network card disconnects and locks up, and requires a reboot in order for it to work again.

Any ideas on how to fix this?

I first encountered a long time ago running windows. When I first got this laptop, I lived in a rural area and accessed the internet using a phone line. So, I didn't have this Linksys wireless card, and wouldn't for quite a while. When I finally moved to the city a few years later, and got this card, this problem started to occur and I noticed that it would happen EVERY time sound was playing through the speakers while at the same time I was downloading or uploading to the internet. I can't remember how the problem was cleared up, but I think it cleared itself up after a service pack update (windows XP was installed at the time), or a fresh reinstall

So now this old problem is back to haunt me, and I'm not exactly sure what causes it. I've got a different card on the way in the mail, and hopefully it won't have the same problem. But I would like to get this solved just for kicks.

---

### Post by tgalati4 on 2007-02-20
Sounds like an interrupt issue.

Post interesting sections of:
dmesg
lspci
ifconfig
iwconfig       (erase any personal network ID info)

Go into your BIOS and turn off Plug-N-Play (PNP), turn off serial port, infra port, parallel port.  This will free up some interrupts to get your network going.

---

