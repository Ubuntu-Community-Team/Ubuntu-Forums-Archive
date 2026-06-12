---
title: "Monitor out of range on boot"
date: 2009-02-05
forum: Hardware
---

### Post by AllRadioisDead on 2009-02-05
Hi, while my pc is booting, just before the login screen, My monitor displays an out of range error. It restores itself when I get to the login screen. I'm currently trying to fix it. I found [this]("http://ubuntuforums.org/showthread.php?t=83973c") thread.
I'm not sure what to put, I know the name of my card, but I'm not sure what goes into the config file.
Here's my current file:
```
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
        Identifier      "Configured Video Device"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection



```
I believe a refresh rate of 75 mhz is what I'm looking for, and my resolution is 1280x1024.
Help would be appreciated!

---

