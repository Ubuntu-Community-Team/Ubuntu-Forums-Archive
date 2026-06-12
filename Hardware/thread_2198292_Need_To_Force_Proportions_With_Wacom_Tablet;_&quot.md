---
title: "Need To Force Proportions With Wacom Tablet; &quot;KeepShape&quot; Doesn't Work?"
date: 2014-01-08
forum: Hardware
---

### Post by Espionage724 on 2014-01-08
I have a CTH-460, and Xubuntu 13.10. The tablet so far works great, but I want to correct the aspect so the tablet properly matches my screen area.

On Windows, ticking the "Force Proportions" box under Wacom's control panel corrected the aspect, and left a small area unused towards the bottom area of my tablet.

On Linux how evever, I can't seem to do this. I've read a guide that said to just put **Option "KeepShape" "on"** in **/usr/share/X11/xorg.conf.d/50-wacom.conf** but this doesn't seem to work (the bottom area of my tablet is still used). I read some 2007 article that said the setting was broken, but hopefully this isn't still the case.

Any ideas what I could do? Apparently I can use the **BottomY** option to set the aspect properly, but have no idea how to calculate such a value. My screen resolution is 1600x900.

---

### Post by Espionage724 on 2014-01-14
Figured it out, kind of silly I didn't think of this sooner though. KDE's Tablet config gives raw numbers when setting proportions. So... I simply booted a LiveCD of Kubuntu, forced the proportions, got the Area numbers via xsetwacom (they vary from the KDE GUI ones), rebooted back to Xubuntu, entered the numbers in xsetwacom, and that was that.

---

