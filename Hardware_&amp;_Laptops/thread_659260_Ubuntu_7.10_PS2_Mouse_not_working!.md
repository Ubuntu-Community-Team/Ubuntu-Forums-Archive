---
title: "Ubuntu 7.10 PS/2 Mouse not working!"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by niqqq on 2008-01-05
my PS/2 mouse does not move in ubuntu. (yes it does in windows Xp)

this problem started ever since the LIVE CD, but i still managed to install it using my keyboard (alt-shift-numlock).

now everything is fine in my newly installed Gutsy Gibbon EXCEPT FOR THE MOUSE!

please help me!

---

### Post by firefox-dm on 2008-01-06
Try editing the "InputDevice" mouse section in your /etc/X11/xorg.conf file:
```
sudo vi /etc/X11/xorg.conf
```
```
Section "InputDevice"
...
        Driver          "mouse"
        Option          "Device"                "/dev/psaux"
...
EndSection
```
Maybe you also need to change the Protocol:
```
        Option          "Protocol"              "ImPS/2" # or "auto"
```
(Of course, you need to have installed xserver-xorg-input-mouse package, but you already have that, I hope).

---

