---
title: "HP Pavilion dv9000 wireless"
date: 2009-12-17
forum: Hardware
---

### Post by freestyleren on 2009-12-17
I have dual-booted my Vista HP Pavilion dv9000 with Ubuntu 9.10. The problem is it doesn't detect any wireless net. I suspect it has something to do with the fact that the wireless switch on the side of my computer seems to be deactivated, regardless of position. Wireless works fine in Vista.

---

### Post by pi4r0n on 2009-12-17
Hello **freestyleren**

**Question No1 **- Does Ubuntu recognise you card
**Question No2** - Do you have the right drivers
**Question No3** - Have you look at any of these [Link 1]("http://ubuntuforums.org/showthread.php?p=6183681") [Links 2]("http://www.google.co.uk/search?hl=en&ei=-k4qS6j9F4XSjAfXk-SiBw&sa=X&oi=spell&resnum=0&ct=result&cd=1&ved=0CA0QBSgA&q=Ubuntu+Wireless+issues&spell=1")

---

### Post by freestyleren on 2009-12-17
I looked under hardware drivers and it seems I don't have any drivers installed.

Apparently I can find them here:
[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&dlc=en&cc=us&product=1842189](http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=2093&lc=en&dlc=en&cc=us&product=1842189)

My question is which ones would I need and how would I install them?

---

### Post by NTHQ on 2009-12-17
Hey I have the same laptop and had that problem too. The light on the switch stays orange right?
The first time I installed 9.10 it couldn't detect any drivers either. After I did a kernel update, it found 2 nVidia drivers and the Broadcom driver for the wireless internet.
If you don't have the latest kernel, connect your modem directly to your laptop using an ethernet cable and go to System > Administration > Update Manager and check for new updates.
That worked for me.

---

### Post by freestyleren on 2009-12-17
Ok, I'll try that when I find a cable. So your wireless net works although the switch is disabled?

---

### Post by NTHQ on 2009-12-17
No it's enabled now. Once I installed the driver the light turned blue.
How far do you need to search for a cable? Just use the one connecting your modem to your router. Just warn everyone else using the Wi-Fi that it will be down for a few minutes.

---

### Post by freestyleren on 2009-12-17
It worked! The light is blue and everything.
Thanks man.

---

### Post by NTHQ on 2009-12-17
Glad I could help. :)

---

