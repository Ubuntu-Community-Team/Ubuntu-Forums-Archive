---
title: "[SOLVED] Abnormally high mem usage on Intel driver?"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by sb73542 on 2008-02-17
Hello,

I'm trying to install a lightweight system with Ubuntu.  When I am using the VESA driver for my Intel 915 (widescreen 1280x800) graphics card, the memory usage of my system at a failsafe graphical terminal is around 40 MB.  But widescreen resolution doesn't work with VESA, so I am forced to use the xorg "intel" experimental driver.  But whenever I use this driver, memory usage is around 140 MB.  Are there any options to reduce memory usage?  It shouldn't require 140 MB or more just to display a failsafe graphical terminal.

Thanks!

---

### Post by sb73542 on 2008-02-18
I'm still fighting with this.  I have read that AGP is what uses the shared system memory.  So is there any way to disable the AGP modules and still let X start up without errors?

---

### Post by Yellow Pasque on 2008-02-19
Does the same behavior occur if you use the i810 driver?

---

### Post by sb73542 on 2008-02-19
With the i810 driver it's almost as high, approximately 110 MB of memory usage.  Again, this is the memory usage from the failsafe terminal, on a very minimal install, with no applications and very few services running.

---

### Post by Yellow Pasque on 2008-02-19
Ok, I see two possibilities
1. Use the i810 driver and try disabling 3d accel and Xvideo with the appropriate options in /etc/X11/xorg.conf (Manual - [http://intellinuxgraphics.org/man.html](http://intellinuxgraphics.org/man.html))
2. Use a tool called 915resolution to alter your video BIOS to support widescreen modes, and then use the VESA driver. There is a package already built for Ubuntu in the repo, so just:
```
sudo apt-get install 915resolution
```
Instructions here: [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

---

### Post by sb73542 on 2008-02-19
Hi again,

Thanks for the reply!  So you think the 915resolution program works with the VESA driver?  I thought it only worked with the i810 driver.  I hope you're right, VESA would be fine for me if only it supported my widescreen resolution.

---

### Post by Yellow Pasque on 2008-02-19
Hmm, you might have a point there. I'm not sure if it needs an intel video driver or not.

EDIT: Also, can you control how much RAM you allocate to video in your system setup/BIOS?

---

### Post by sb73542 on 2008-02-19
No, there is no BIOS setting for the video RAM.  And it says it only uses 8 MB anyway!  From what I've read, agpgart is responsible for using the shared memory for video purposes.  I did try to use NoAccel and not load glx with the i810 driver, and I even tried to use the "VideoRAM 4096" option, but it ignores it.

---

### Post by sb73542 on 2008-02-19
Well, Temüjin, that was a good tip, 915resolution DOES work with the vesa driver.  I now have a nice Gnome desktop with 1280x800 resolution that uses less then 80 MB at startup.  Thanks!

---

### Post by Yellow Pasque on 2008-02-19
Nice! Glad to hear my shot in the dark hit the target :P

Please mark thread as SOLVED (under the Thread Tools menu) so that people might be able to find a solution easier when they're searching.

---

