---
title: "No video after initial splash screen - Ubunto 9.04"
date: 2009-10-24
forum: Installation &amp; Upgrades
---

### Post by dans1337 on 2009-10-24
Disclaimer: Last time I installed a Linux Distro, it was Red Hat 6.1, so I'm not up to date on my linux skills. Also, I searched the forums for Core i5, and EAH4670, but came up empty.
 
Anyway,
 
I installed Ubuntu 9.04 - 64bit on my Athlon FX system 2 days ago, and I must say that every thing worked flawlessly. I was impressed. :KS
 
However, now I am trying to get Ubuntu 9.04 installed on my brand spankin new Intel Core i5 system, and I seem to have some trouble.
 
I tried the amd64.iso installer first, and I actually got the installer to run after staring at darkness for about 10 minutes. Finally the install screens came up, and I was able to complete the drive partitioning and what not. After rebooting, I see the Ubuntu splash screen, and then... nothing. I hit the power button on my case after waiting about 10 minutes, at which time the Ubuntu system went through a normal shutdown process. So, I guess the kernel was alive, I just had no video.
 
I tried running the Live CD with the x86 32bit .iso, and that gave me nothing after the splash screen as well. That one would not shut down, I had to cold reboot.
 
I am guessing that my video card may not be supported, but I am not sure how to proceed. Any tips would be greatly appreciated.
 
Hardware:
CPU: Intel Core i5-750
Motherboard: Gigabyte P55M-UD4
4GB DDR3-10666
Video: Asus EAH4670 (ATI Radeon HD4670)

---

### Post by dans1337 on 2009-10-25
Well, I booted into Safe Graphics Mode using the 64-bit CD, and reinstalled from scratch.
 
Ubuntu loaded after warning me that the display drivers were hosed, and let me in. After that, I was able to update the system, and found the ATI drivers in 'Hardware Drivers'. Downloading the drivers was a little strange, I saw a 'Jockey' crash, and it appeared to have done nothing with the drivers. But, after a reboot... everything works.
 
Fantastic! I love this stuff. Now, to get Virtual Box working...

---

### Post by sunh11373 on 2009-10-28
How do you connect your monitor to the graphic card? DVI/VGA/HDMI? I have the same graphics card and have the same issue with DVI connection.

-thanks

---

### Post by dans1337 on 2009-11-02
I am using the DVI connection also.

Edit: I should add that I am having trouble with 9.10, the display flickers between the desktop and the ubuntu splash screen. I'm not yet sure if it's because I'm running it as a VM or not.

---

### Post by devehf on 2009-11-07
I just switched from the DVI to HDMI port on my ASUS mobo because the DVI port blacked out intermittently. So far so good with the HDMI port.

I have an ATI x1200 (RS690 chiptset) embedded on this board. I'm using the open source default drivers on Koala Studio.

---

