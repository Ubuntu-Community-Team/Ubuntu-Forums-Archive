---
title: "Wireless connection drops."
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by buddachile on 2005-08-29
Tyrial wrote: *My wireless keeps droping out overnight when I leave stuff to download, whenever I watch a movie or do something in fullscreen. Now the thing is it doesn't drop out if I'm just browsing web pages. I'm posotive it isn't connection strength because in Windows it reports it as full strength and I can download for days at a time without worrying about it dropping out. It's a D-Link DWL-G520+ connecting to a Billion 7500G modem, in device manager it is coming up as ACX 111 54Mbps Wireless Interface. If any other info is need (and I'm guesing it will be) just ask and tell me how to get it because I'm still a bit of a noob, thanks.*

 i'm having similar problems with my new dell inspiron 600m laptop. the wireless device is a built in intel prowireless 2200bg.

i just installed ubuntu on it last night (the laptop is dual booted with xp). at first, wireless seemed to be working fine. i have a d-link 520 wireless router set up w/ 64-bit wep & mac address filtering & ssid not broadcasting. it appears that if i don't use my network connection for a while it just drops and i cannot re-establish it without a reboot. i tried using the network-admin gui but that didn't help. also tried "ifdown eth1; ifup eth1" but no dice.

i didn't do anything special to get wireless working in the first place. no ndiswrapper that i can tell was intalled. also, i am near the access point, so my signal is very strong.  i don't have this problem at all when booted in xp with the same laptop.

i'm really confused. any thoughts?

---

### Post by gravestone on 2005-08-29
It sounds like a power management problem. If you are surfing the net, the mouse is being moved. When leaving it for long downloads, the power management thinks the laptop is not being used and may be shutting down the wireless card. Try first in the BIOS set up, as this is the biggest cause of the problem.

Next check your power management settings. I'm running KDE, so I'm not sure where you'll find them in Gnome.

---

### Post by snop on 2005-08-29
[QUOTE=gravestone]It sounds like a power management problem. If you are surfing the net, the mouse is being moved. When leaving it for long downloads, the power management thinks the laptop is not being used and may be shutting down the wireless card. Try first in the BIOS set up, as this is the biggest cause of the problem.

Next check your power management settings. I'm running KDE, so I'm not sure where you'll find them in Gnome.[/QUOTE]
 This is a know issue with ipw2200 driver. Install a new version (there's a tutorial from luca_linux here [http://www.ubuntuforums.org/showthread.php?t=26623&highlight=wireless+connection+drops](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=wireless+connection+drops))

You should have searched through this forum before posting.

SnOp

---

### Post by buddachile on 2005-08-29
[QUOTE=snop]This is a know issue with ipw2200 driver. Install a new version (there's a tutorial from luca_linux here [http://www.ubuntuforums.org/showthread.php?t=26623&highlight=wireless+connection+drops](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=wireless+connection+drops))

You should have searched through this forum before posting.

SnOp[/QUOTE]

i apologize for the redundant question.  i did originally search the forum
and in fact i found the thread with the howto (ipw2200 + wpa), but i g listing uess i
didn't use a good combination of search terms.

when i read the howto i was tempted to upgrade to the new driver but
i found the procedure to be a bit involved and i would end up with a non
standard ubuntu install. fearing difficulties updating my install in the future
i became inclined to wait until the new driver was available via apt-get.

is my fear unfounded? that is, if/when ubuntu comes with the newer driver
will it be easy for me to get back to having a standard install where i can
update everything with apt-get?  sorry if this is a stupid question.

---

### Post by luca_linux on 2005-08-29
Don't worry, go with the upgrade.

---

