---
title: "LG R700 videocard drivers for 8600m GPU"
date: 2008-09-15
forum: Hardware
---

### Post by Kossilar on 2008-09-15
Hello folks. 

I have an R700 laptop from LG and I just installed Kubuntu 8.04. The computer has an 8600m videocard in there, but I can't seem to find working drivers for it. I tried to use the regular 8600 drivers, but it froze my system and the NVIDIA page doesn't list 8600m drivers even for Vista computers(this system originally came with Vista).

Any idea what I should use to get my system running with the proper videocard drivers?

EDIT: It seems the videocard drivers are provided by LG. That's annoying. Does anybody know what can be done to get accelerated graphics for my laptop?

---

### Post by pelle.k on 2008-09-19
My lg r500 has a 8600m gs, and i use the "nvidia" proprietary driver. However, you've got a 8600m gt right? There should be no problems as i'm running a 8600 GT on my desktop computer, but you might want to try installing a more recent video card driver with the help of "envy". It's in the repos.
You should also have proper suspend/hibernation after that.

---

### Post by Kossilar on 2008-09-22
Hmmm. Apparently, even though the Nvidia website doesn't actually mention drivers for the 8600m, the 8700m drivers appear to have support for my card. That seems to solve the problem. Now if I can only get the drivers to actually load on boot, everything should be golden.

---

### Post by pelle.k on 2008-09-22
It's the same driver for all 6,7,8 and 9 series btw. There's no specific driver for a 8700m. It is the same driver that i'm using.
If you enable nvidia in "hardware driver manager", it is activated on boot.

Can you be more specific?

---

