---
title: "damaged contens of gnome-system-monitor window"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by kapetr on 2009-11-11
After upgrade to 9.10, the  gnome-system-monitor window is unreadable.
It also affect "status box" of UbuntuOne client. Maybe also other things ...

See attachments.

Any Idea ?

---

### Post by mac9416 on 2009-11-11
Hey, kapetr,

This is a well-known problem with the open source ATI driver on laptops (most notably older IBMs) running Radeon Mobility 7500. You can read plenty about it here: [http://ubuntuforums.org/showthread.php?t=1285406](http://ubuntuforums.org/showthread.php?t=1285406)

There are two possible fixes. One is to turn visual effects to "Normal" in System > Preferences > Appearance > Visual Effects. This has worked for some, but not for others.

If that does not work, you can enable the "vesa" driver. You will lose hardware acceleration (which I understand means more sluggish effects, lower game performance), but you will get System Monitor and notifications back. Edit /etc/X11/xorg.conf...

```
$ sudo gedit /etc/X11/xorg.conf
```

...to look like this...

> Section "Device"
Identifier "Configured Video Device"
Driver "vesa"
EndSection

Section "Monitor"
Identifier "Configured Monitor"
EndSection


Section "Screen"
Identifier "Default Screen"
Monitor "Configured Monitor"
Device "Configured Video Device"
EndSection

...then reboot.

I have reported a bug about this, without results so far. [https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/440608](https://bugs.launchpad.net/ubuntu/+source/gnome-system-monitor/+bug/440608)

Hopefully one of those fixes it for you!

---

### Post by kapetr on 2009-11-13
Thank You for explanation.

I use ATI Radeon 7000 AGP on my desktop PC (Athlon XP2000+, VIA KT133A chipset).
I do not use any effects - my card is too slow for it.

I often play videos on my PC and even with accel. graphic it is often too demanding for my PC, also I can't use vesa driver.

I hope, that this bug will be fixed in future.

Thanks  kapetr

---

