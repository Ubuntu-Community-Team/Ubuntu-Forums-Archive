---
title: "low resolution after installation"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by DemiAlbedo on 2009-03-28
I am currently running Kubuntu 8.10 KDE 4. 

I installed Kubuntu fine with no problems however when I booted into Kubuntu my resolution was set to 800x600 and I can't make it go any higher. I checked all the default areas for resolution setup (System >> System Settings & KRandRTray. 

I Know my resolution can go higher because currently there is a at least 1inch of black around my screen because it is not max resolution. 

I tried dpkg -reconfigure xserver-xorg, editing xorg.conf, xrandr (no idea how that program is suppose to work) and even envyng -qt and still nothing except broken xorg file and messed up .ICEauthority files.

This is the video card information i get from lspci. VGA compatible controller: Trident Microsystems CyberBlade XPAi1. When i check device hardware (which i usually do to fix graphic card problems) to turn on the driver for this graphic card nothing is there. Its like the system can see the graphic card but won't turn it "on" and won't allow me to turn it on.

Any advice would be appreciated.

---

### Post by DemiAlbedo on 2009-03-28
Just a little more information, here is my /etc/X11/xorg.conf file

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

As you can see it is not adding any graphic card information and I can't go to the restricted drives and find the graphic card there. I'm  willing to use an open source driver i don't care as long as I can get my resolution back.

---

### Post by DemiAlbedo on 2009-03-28
New update.

I keep getting told that dpkg-reconfigure xserver-xorg should fix the problem.

When I run that command I get ONE screen that mentions anything about video options. It mentions something about video framerate buffering. . .select yes or no. Sorry I can't recall specifically what it said. After that screen there is maybe 5 more screens all that have to do with keyboard layout. I know that is also not normal because other forums keep mentioning about how you can adjust colour depth and drivers, but I don't get any of those options. I tried selection Yes & No at the framerate screen hoping for more options.

---

### Post by brayden13 on 2009-03-28
I think I know exactly what has happened. I had this too. Did you install the video card drivers? (if any)

Once you installed them (assuming you are lucky enough to have you video card supported) you should be able to set your resolution to the resolution that suits you the best. Rather than 800x600.

---

### Post by zolek78 on 2009-03-29
i have the same problem and it still could not be solved even when i've tried to install the driver. i'm using Nvidia GeForce 6800

---

