---
title: "NVIDIA Driver install help"
date: 2008-11-27
forum: Hardware
---

### Post by Johny79 on 2008-11-27
After much searching I found a blog where someone had fixed the "white screen of death" issue with the 8600M GT, but I can't seem to get it to work for me :(

I've downloaded NVIDIA-Linux-x86-173.14.09.pkg1.run, then removed the nvidia-glx-new package (which I would assume has removed the nvidia driver?).

Now I press ctrl+alt+F1, login, and try to run "sudo /etc/init.d/gdm stop", however it says "not found" rather than stopping X server as it was supposed to.

I've Googled and search the forum but found no solution, everyone seems to just say that the command should work, I can't install the driver without stopping X so I'm pretty screwed at the moment, can anyone tell me where I'm going wrong?

---

### Post by Johny79 on 2008-11-27
Ok so I found out that for some reason that command only works in some installations (no idea why though?!) so had to use...

sudo killall gdm

...instead.

That worked and the driver installed etc (well after installing "build essentials").

Now after restarting I'm stuck in 800x600 resolution, it asks me to manually specify the screen and graphics card, which I did, but it's completely ignored.

Re-enabling the Nvidia driver through "Hardware Drivers" gives me the dreaded "white screen of death" again, so I'm worse off than when I started :(

I'm starting to think I might have to give up on the idea of running Ubuntu on my laptop, after all I've been trying to resolve this for 6 months now :(

---

