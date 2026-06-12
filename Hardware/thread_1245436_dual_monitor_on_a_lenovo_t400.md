---
title: "dual monitor on a lenovo t400"
date: 2009-08-20
forum: Hardware
---

### Post by mlilien on 2009-08-20
I recently got a new laptop (ATI Mobility Radeon 3470 with 256MB graphics), running Jaunty 64bit, and have been trying to configure it to use a second, external monitor.  When I plug it in and turn on my computer, the external monitor is a mirror of my primary.  ATI catlyst control center detects both monitors and has the proper resolution for them, but gives me no options for a dual screen.  When I try to open System->Preferences->Display, an empty window comes up and the rest of my display functions (typing, moving windows, etc) start to lag.

I've tried to follow several tutorials, but my results are frequently different than what they get.

When I run sudo dpkg-reconfigure -phigh xserver-xorg with my external monitor plugged in and turned on, but I only get the following written to xorg.conf:
Section "Device"
    Identifier  "Configured Video Device"
EndSection

Section "Monitor"
    Identifier  "Configured Monitor"
EndSection

Section "Screen"
    Identifier  "Default Screen"
    Monitor     "Configured Monitor"
    Device      "Configured Video Device"
EndSection


I also tried playing with xrandr, which detects my monitor as CRT1, rather than VGA.

Thanks in advance for any help,
Mark

---

