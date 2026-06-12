---
title: "Cannot login without external monitor: xserver-xorg-video-intel"
date: 2007-09-26
forum: Hardware &amp; Laptops
---

### Post by ekirby on 2007-09-26
I am having an interesting problem with xserver-xorg-video-intel.  With this video driver, I can use an external widescreen LCD just fine.  However, I can't login to the laptop without an external monitor plugged in.  GDM shows me the login screen.  My username and password go through, but as soon as they do, I get kicked back to the login screen.

Even more interestingly, if I boot without the monitor plugged in, wait until the GDM login screen pops up, and then plug in the external monitor, I can log on and see everything on the laptop screen at the proper resolution!

Apparently, something about the Intel driver is expecting something to be plugged into the VGA output.

The standard solution is to use xserver-xorg-video-i810 instead of the intel driver.  However, I have not been able to get the i810 driver to support my external widescreen LCD's 1680x1050 resolution.

machine: HP Pavilion dv4170
video chipset: Mobile 915GM/GMS/910GML Express Graphics Controller
system: Feisty (Ubuntu 7.04) kernel 2.6.20-16-386 #2

This person is having the same problem:
[http://ubuntuforums.org/showthread.php?t=480730]("http://ubuntuforums.org/showthread.php?t=480730")

Thanks for your help!
Evan

---

