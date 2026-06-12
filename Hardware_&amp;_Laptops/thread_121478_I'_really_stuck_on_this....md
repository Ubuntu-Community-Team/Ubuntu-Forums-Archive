---
title: "I' really stuck on this..."
date: 2006-01-25
forum: Hardware &amp; Laptops
---

### Post by spock2263 on 2006-01-25
Hi to everyone.
I'm really stuck on this:
I've an Acer Aspire 1693WLMi with ATI MOBILITY RADEON X700 PCI Express with 128MB VRAM. My monitor is 16:9 widescreen monitor.
I've installed 5.10 and although I chose 1280x800 resolution during installation, now it only gives me 1024x768, which is for a 4:3 monitor, so everything is streched to fit the wide screen. I run the xorg.conf file and confirmed that the resolution is set to 1280x800, I also run dpkg reconf. and I set again the right resolution, still no luck. Everything is ok in the xorg.conf file but still I have 1024x768.....
Please please please help me, it has given me a real headache for weeks...

---

### Post by rjwood on 2006-01-25
Have you gone into system>preferences>screen resolution and tried there? If so then it must have something to do with configuration or hardware incompatability somewhere..Good Luck

---

### Post by frodon on 2006-01-25
Could you post your xorg.conf file here ?

Generally you have to add the horizontal and vertical refresh rates of your screen to avoid this kind of problems, see this guide for details : [http://www.ubuntuforums.org/showthread.php?t=83973](http://www.ubuntuforums.org/showthread.php?t=83973)

---

