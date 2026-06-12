---
title: "xubuntu 8.10 freezes on boot after software update"
date: 2009-04-20
forum: Installation &amp; Upgrades
---

### Post by thetrivialstuff on 2009-04-20
System parameters:
Xubuntu 8.10 desktop install CD
Old hardware - Athlon 800MHz, really old ATI Rage Pro graphics

The install went fine, and the system booted normally. I then ran software update, rebooted, and the system froze during the part where the boot logo screen is a progress bar (just after the part where it imitates Windows XP with the little section that's not really a progress bar).

Flipping to other consoles revealed that it had frozen on "Loading hardware drivers..." Some other threads advised waiting until it unfroze on its own, but it didn't.

Looking at the grub menu options next boot, I saw that I now had kernel versions 2.6.27-7 generic and 2.6.27-11 generic -- I assume that -7 was the one from the initial install. I tried it and it booted, but there were some graphics anomalies (flickering lines).

After some more investigating, I found that 2.6.27-11 booted OK if I removed "quiet" from the kernel parameters and changed "splash" to "nosplash".

So, hopefully that helps somebody -- looks like 2.6.27-11 likes to be heard when it starts :)

---

