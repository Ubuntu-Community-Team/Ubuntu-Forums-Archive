---
title: "NVIDIA drivers stops xorg.conf"
date: 2007-07-08
forum: Hardware &amp; Laptops
---

### Post by joels on 2007-07-08
Hi all,
I have to admit to being a complete newbie to the linux world, but am picking up all that I can. I'm running Ubuntu 7.04 and is completely updated.
I'm dual booting with windows xp. I've got two video cards and monitors - a GeForce4 MX 440 (AGP 8x I beleive) and a much older Riva 128.
Everything is displayed on the Geforce connected monitor for the BIOS, GRUB, and the ubuntu loading screen, but upon login, everything is displayed on the Riva 128 for all of linux.
So I tried to update the drivers and install and enable the nvidia-glx drivers through the "restricted drivers manager", but when I reboot it all crashes (the xorg.conf file or process I assume), saying

(WW) NVIDIA: No matching Device section for instance (BusID PCI:1:0:0) found
(EE) No devices detected.

Fatal server error:
no screens found

I've installed xorg-edit, and according to it, the riva 128 card is on busID PCI:0:8:0. It doesn't display anything about my Geforce card.
 I've looked around, and can see that there are a lot of problems with these NVIDIA cards, but can't find any answers to my problem. Any help would be most appreciated. I've included as much info as I could to help (sorry if its too much) Thanks all.


Edit: Got it working, finally.

---

