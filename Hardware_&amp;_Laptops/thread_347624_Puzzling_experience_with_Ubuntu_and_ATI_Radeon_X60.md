---
title: "Puzzling experience with Ubuntu and ATI Radeon X600 video card"
date: 2007-01-27
forum: Hardware &amp; Laptops
---

### Post by RCC2k7 on 2007-01-27
One of my computers has an ATI Radeon X600 HyperMemory video card. On this system Ubuntu 6.10 would not start at all - even the Safe Graphics Mode gives me a distorted text-based screen, where among all sorts of funky characters, I can get that the X Server couldn't start and from the log, it says "No Screens found".

On this same computer, Ubuntu 6.06 will only start in Safe Graphics Mode _but only if I also select Spanish as the language in the initial CD boot screen._ Other languages might work, but English definitely fails to load even in safe graphics mode. 6.10 won't start at all in either language.

I took the risk of installing 6.06 after starting the system in Spanish and with Safe Graphics Mode. The install went well and once installed, I could switch the OS language to English and the system still booted OK. So I took yet another risk and upgraded 6.06 to 6.10 using the online download. The upgraded completed successfully and the system is still booting OK.

Has anyone else experienced similar problems with ATI Radeon X600 or other cards? Now I'm worried that my Ubuntu system can stop booting at anytime with a graphics failure, especially if I keep downloading online updates.

---

### Post by JustBrowsing on 2007-01-27
> **RCC2k7 said:**
> 
Has anyone else experienced similar problems with ATI Radeon X600 or other cards? Now I'm worried that my Ubuntu system can stop booting at anytime with a graphics failure, especially if I keep downloading online updates.

Yes, I have a ATI Radeon x600 in my Dimension E510, and the video card and wireless card (which is a problem with most installs) are problems when first installing Ubuntu.

If you do a search, you'll find a workaround to installing Ubuntu 6.06 and 6.10 which will let you install ATi FLGRX drivers and you'll be on your way.

---

