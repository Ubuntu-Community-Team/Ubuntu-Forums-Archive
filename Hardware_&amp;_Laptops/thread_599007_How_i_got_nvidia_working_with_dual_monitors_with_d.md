---
title: "How i got nvidia working with dual monitors with different sizes"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by thepineApple on 2007-10-31
After nearly two days of..googling, trying, struglling, pulling off my hair, I finally got my nvidia 7100GS working with my two LCDs: Acer 22 inch wide screen (1680x1050) + 19 inch Sony normal screen (1280x1024). thought i might as well share this experience just to help anyone out there who's trying the same or similar conf.

Step by step:
1. Boot into gusty, doesn't matter one or two screens, as long as you can log in and install the nvidia 100.14.19 driver (or the one that suits your video card). I'm not a guru YET, so i just used the GUI from System-> Admin -> Restricted driver manager.
2. After installing the new nvidia driver, reboot the computer and go into the safe mode (2nd line in GRUB). once you are in as root, type "dpkg-reconfigure xserver-xorg" this will reconfigure the xserver for you, follow the steps. NOTE; in the 2nd selection menu where it asks which driver to use, select "nvidia" INSTEAD OF "nv", this is the new driver you just installed, I just set the rest to the default. At last reboot again.
3. Now you should have the correct resolution working on your main screen (mine is the 22 inch), login as yourself and open up a console and type "sudo nvidia-settings", this will bring up the nvidia control panel, a nice GUI as many people have mentioned. just simply enable the second monitor and use nView. after this, a FINAL reboot. (as soon as you enable the second monitor, it should light up already , only  that the resolution and the whoel desktop looks a bit weird. just give it a reboot and you are set)
4. Now both monitors should be working properly.

If any questions i'll try my best to help

cheers:guitar:

---

