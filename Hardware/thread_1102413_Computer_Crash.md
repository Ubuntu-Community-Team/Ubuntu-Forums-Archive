---
title: "Computer Crash"
date: 2009-03-21
forum: Hardware
---

### Post by JWillo on 2009-03-21
Ok, here's one to wrap your collective minds around.  I'm running Ubuntu 8.1 on a Dell Latitude D600 with an Intel Pentium M 1600 mhz processor, a radeon 9000 mobile video system and a 40 gig hdd and 512 mb of ram.  Everything was working fine, then all of a sudden my comp crashed.  Upon restart, the Dell loading screen came up and loaded fine, but then all I get is "Missing Operating System" at the top of my screen.  I've tried re-installing Ubuntu from the cd, but it still recognizes that it's installed on my hdd.  I've even formatted the hdd and re-installed completely from scratch and upon restart, there it is again "Missing Operating System."  I need some serious help here.

---

### Post by charrah on 2009-03-21
I *think* that is what the windows bootloader, ntldr, says when it can't find windows. Which would mean GRUB isn't actually being installed to the MBR? So I would try installing GRUB again in the livecd.

---

### Post by JWillo on 2009-03-21
Found out that it was trying to load from the USB for some reason. Thanks for the help anyway. :D

---

