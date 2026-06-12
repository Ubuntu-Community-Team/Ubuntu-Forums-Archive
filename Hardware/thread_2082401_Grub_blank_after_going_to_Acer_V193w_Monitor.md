---
title: "Grub blank after going to Acer V193w Monitor"
date: 2012-11-09
forum: Hardware
---

### Post by SunfireSSR on 2012-11-09
Ubuntu 12.04 worked great until I swapped the monitor to an Acer V193w (16:10). Grub is blank but works if you let it run. If you hit the <down key> or <tab> before Grub boots, you can see the Menu and make your choice in any resolution you set it at. Have tried rebuilding GRUB after the change to see if any video changes fix the issue. I have GRUB setting gfxmode=640x480 with both monitors. Changed it to 1024x768 and 1440x900 (Native). Tried the "Force Grub to show up" settings I found. That didn't work. 
What appears to be happening is that when GRUB is trying to boot, the monitor is trying to auto-config itself at the same time, and GRUB isn't getting to see its setting. I can't find anything that will tell GRUB to not timeout or have it wait until the auto-config is done. Can't find anything to tell the monitor to boot to a default. Any ideas?

---

### Post by grahammechanical on 2012-11-09
It is my understanding that Grub is designed to work at basic video resolutions on any monitor installed. It is only later when the OS begins to load that the monitor is probed to determine its optimum video configuration settings.

Can you load an operating system? Can you load Ubuntu? You might need to upgrade to a newer video driver. But I do not think that would affect the Grub menu.

Are you sure that you are seeing the Grub menu. It is my understanding that right shift and Esc are the keys to bring up the Grub menu.

What do you mean that Grub works if you let it run? Do you only have one OS on this machine.

Regards.

---

### Post by SunfireSSR on 2012-11-09
I have XP and Ubuntu both on here. Both OS's load and run, no problems there. Just can't see the Grub Menu if I let it take its normal course as set. I can see it if I keystroke for it to show up.

---

### Post by SunfireSSR on 2012-11-10
Can I add some kind of wait statement to grub.cfg to give the monitor time to get set ? And if so, what command, Wait, sleep ?

---

