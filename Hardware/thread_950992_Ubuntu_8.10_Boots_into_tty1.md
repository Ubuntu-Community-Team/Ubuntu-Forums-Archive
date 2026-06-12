---
title: "Ubuntu 8.10 Boots into tty1"
date: 2008-10-17
forum: Hardware
---

### Post by TaylorHelferty on 2008-10-17
I just upgraded to Ubuntu 8.10 (I did a fresh install before this and the same thing happened) and after the loading screen, it went directly into the tty1 console and said something about "no resume image found." I Googled around for a bit and found a few solutions including restore mode, dpkg-reconfigure xserver-xorg, and another trick involving fstab. None of these worked and I can't boot into the GUI. startx and /etc/init.d/gdm restart don't work either. 

This happened in the Alpha release but only after a couple of reboots. A fresh install of the latest Alpha worked fine, but then stopped after an update, and the Beta disc won't even go into the GUI. The disc tells me I'm running in low graphics mode then takes me to tty1, but doing the upgrade doesn't even give me that. Any help would be greatly appreciated. I miss my Ubuntu.

My video card is an ATI Mobility Radeon HD 2400. It worked relatively fine (relatively as in I could do desktop effects, but then applications like Google Earth would flicker) in 8.04 so I don't see how it could be the problem.

---

