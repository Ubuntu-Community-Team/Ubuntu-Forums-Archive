---
title: "Laptop screen drivers/resulotion -- clueless"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by A-dogg on 2008-01-05
Okay, so I made the mistake of digging around where I shouldn't have.

I have a vaio vgn-fs742/w laptop. when I first installed gutsy, the system figured out the correct way to set up the monitor. yesterday, though, I was playing around (always a bad sign) and fiddled with the settings. When I rebooted, the changes took effect and I was stuck in ultra-low resolution and couldn't get out. none of the drivers I selected (I'm doing all this from the "administration-->screens and graphics", not from the command line) would work. finally, I got it going by selecting the intel experimental modesetting graphics card and the screen to "LCD 1280x1024, resolution 1280x800 at 60Hz".

Problem is, everything's small now (I'm guessing because the resolution is set so high?) -- but I'm afraid to change anything again.

can anyone advise what the settings should be? It's a 15" (~14.5") widescreen lcd laptop monitor.

what do the different Hz settings mean?

---

### Post by Yellow Pasque on 2008-01-05
Try this first. Boot into recovery mode (grom the GRUB screen). Login and run:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
When you're done, reboot.

If you're still borked, post your /etc/X11/xorg.conf here.
```
gedit /etc/X11/xorg.conf
```

---

