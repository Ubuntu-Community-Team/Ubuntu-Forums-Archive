---
title: "Would Like to have 1280x1024 resolution"
date: 2009-04-26
forum: Hardware
---

### Post by marionspd on 2009-04-26
I just upgraded my laptop to 9.04.  I was using 8.10.  I bought a new hard drive and installed from live cd.

Since upgrading I am no longer able to change my resolution to 1280x1024.  1024x768 is the highest it will go under the display preferences tool.  Below is my xorg.conf (not much in it).  I've been using Ubuntu for less then a year and I really like it.  Any help is greatly appreciated.

Dell Latitude D610, 1GB ram, 160GB HD


Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

---

