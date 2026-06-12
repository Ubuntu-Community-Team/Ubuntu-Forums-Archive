---
title: "Bamboo Fun Tablet randomly stops working?"
date: 2009-10-04
forum: Hardware
---

### Post by TheChewanater on 2009-10-04
My Wacom Bamboo Tablet stopped working on Ubuntu today.  Neither the pen nor the mouse works, and the light is on, so it's not a hardware problem.  It's worked perfectly fine up to this point.  

I have the linuxwacom xorg drivers and wacom-tools installed.  I've done searches and found this same problem many times, but none of the solutions worked for me.

This is my xorg.conf:
```
Section "Device"
    Identifier    "Configured Video Device"
    Option        "UseFBDev"        "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom"  
  Option        "Type"          "stylus"
  Option        "USB"           "on"         
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom"    
  Option        "Type"          "eraser"
  Option        "USB"           "on"        
EndSection
```I'm on Ubuntu 9.04 on Linux Kernel 2.6.28-15.

---

### Post by Favux on 2009-10-04
Hi TheChewanater,

Your xorg.conf looks fine, although it doesn't have a pad section.  I thought the Bamboo had a pad.  I gather you don't have a Wacom mouse (the cursor section).

While you can use xorg.conf in Jaunty you are "suppose" to use the HAL/.fdi method.  What you give up with xorg.conf is usb hot plugging.  So maybe something interrupts the usb signal, and since you don't have hot plugging, it doesn't reconnect?

You could try the old "pseudo" hot plug commands:  ctrl+alt+F1 and then ctrl+alt+F7

Or you could go from xorg.conf to a 10-wacom.fdi.  See post #176 here:  [http://ubuntuforums.org/showthread.php?t=967147&page=18](http://ubuntuforums.org/showthread.php?t=967147&page=18)

Although I would think if the xorg.conf fails then the default 10-wacom.fdi the default Jaunty linuxwacom drivers install would take over and you'd at least have the stylus.  Did you install another version of linuxwacom?  In Synaptic Package Manager is the 0.8.2-2 wacom-tools installed?

---

### Post by TheChewanater on 2009-10-04
No, everything is in check.

I'll try a reload, since it worked with a fresh install.

---

### Post by TheChewanater on 2009-10-05
I figured out the problem (I think).

It worked fine with a fresh install, but stopped working when I put it into Suspend then started it up again.  That's what I did right before it stopped working the last time.  That's weird.  How can using suspend mode make the tablet stop working until I completely reload it?

I can reload it again and not use suspend for now, but I really want to figure out what's wrong since I use suspend mode a lot.

---

