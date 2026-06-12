---
title: "laptop resolution problems"
date: 2009-05-16
forum: Installation &amp; Upgrades
---

### Post by yoma819 on 2009-05-16
hello all
i have just installed ubuntu on my laptop and every time i go into the display settings to try and up the resolution it just readjusts my screen size!
as in it makes the display area of my screen smaller not the resolution!
the strange thing is that it did nt need to install any third party restricted drivers for my screen!
here is my xorg.conf


#   sudo dpkg-reconfigure -phigh xserver-xorg

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



all the graphics seem to be running slowly like they would on xp before the drivers were installed!
any help would be great
thanks
yoma

---

### Post by yoma819 on 2009-05-16
bump

---

