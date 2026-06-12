---
title: "Strange colors on screen on Dell Inspiron 8200"
date: 2007-12-21
forum: Hardware &amp; Laptops
---

### Post by raam on 2007-12-21
Hello!
I just installed Ubuntu on my Dell Inspiron 8200 laptop.  The screen on the laptop is broken, and so I have it connected with a VGA cable to a Samsung Syncmaster 931B 19" monitor.  After the install, the screen only shows random colored blocks that change all the time - nothing is readable - just all these colored rectangles.

My friend tried to help, but with no luck.  Running 'lspci | grep VGA' gives:
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go] (rev a3)

He tried fixing it by running "sudo dpkg-reconfigure xserver-xorg" and using all of the defaults, but no luck.  I'm using a different computer to type this, so it's hard to post the entire xorg.conf, but here's some important parts:

Section "Device"
Identifier "nVidia Corporation NV17 [GeForce4 440 Go]"
Driver "nv"
BusID "PCI:1:0:0"
EndSection

Section "Monitor"
Identifier "SyncMaster 931B"
Option "DPMS"
HorizSync 30-65
VertRefresh 50-75
EndSection

Section "Screen"
Identifier "Default Screen"
Device "nVidia Corporation NV17 [GeForce4 440 Go]"
Monitor "SyncMaster 931B"
DefaultDepth 24
SubSection "Display"
Modes "1024x768" "800x600" "640x480"
EndSubSection
EndSection

Any help would be greatly appreciated!  Also, I'm totally new to Linux, so simple instructions would be very appreciated!  Thanks in advance!

---

