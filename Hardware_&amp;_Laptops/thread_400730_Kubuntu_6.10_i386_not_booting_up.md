---
title: "Kubuntu 6.10 i386 not booting up"
date: 2007-04-03
forum: Hardware &amp; Laptops
---

### Post by kristjans on 2007-04-03
can anyone tell why kubuntu's log in screen might not appear after the loading screen and a black screen comes up instead? the system is a laptop with amd turion x2 and nvidia gfx card.

safe mode gets stuck at "checking TSC synchronization across 2 CPUs". win xp works fine.

---

### Post by kristjans on 2007-04-20
Trying Feisty Fawn now. It seems to get a black screen when the graphical interface turns on. In Feisty, the "safe mode" does work. In there, it gets a black screen when logging out and closing the graphical interface. **It didn't work off the live CD** with the same problem. The alternate install CD had to be used. However, it turned on the first time to normal mode. After the first reboot (and black screen+repeating sound) it stopped working.

Laptop: 
HP Pavilion DV6119US (DV 6000 series)

Processor: AMD Turion 64x2 Mobile TL-50
Memory: 1 024 MB RAM
Graphics card: NVIDIA GeForce Go 6150
Sound card: Conexant
Network: NVIDIA nForce  
Wireless card: Broadcom BCM4301

---

### Post by calraith on 2007-04-20
In /boot/grub/menu.lst, try removing "quiet splash" and whatever vga= parameter might be there (if any) from the kernel line near the bottom of the file, so that the only kernel option remaining is "ro."  That should allow you to watch the kernel messages as the system initializes.  Are you getting a kernel panic?  Does the kernel panic reference any sort of hardware bug, and give you any suggestion to work around the problem?

If no kernel panic, if your display simply goes black when X tries to start, boot into single user and install nvidia-glx and nvidia-kernel-common, and update /etc/X11/xorg.conf to load driver "nvidia" instead of driver "nv."

After you've finished troubleshooting your system, it should be safe to re-add "quiet splash" and any vga= parameter you might've had before.

---

### Post by kristjans on 2007-04-20
Thank you. The issue seems not to be kernel panic, as it goes through all the text and *after* that the screen turns blank.

E: Thank you! Changing the drivers worked out perfectly!

---

### Post by kristjans on 2007-04-20
Thank you. The issue seems not to be kernel panic, as it goes through all the text and *after* that the screen turns blank.
E: I'll try the NVIDIA suggestion now.

---

