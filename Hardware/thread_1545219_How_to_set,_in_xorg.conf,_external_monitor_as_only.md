---
title: "How to set, in xorg.conf, external monitor as only one when plugged in"
date: 2010-08-03
forum: Hardware
---

### Post by equaeghe on 2010-08-03
On 10.04

How do I set, in xorg.conf, the external monitor as the only active one when it is plugged in? (Dual head will not work because of [bug #559883]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/559883"))

My current xorg.conf (vga=external):

```
Section "Device"
    Identifier  "i945GM"
    Option  "monitor-LVDS1"  "lvds"
    Option  "monitor-VGA1"   "vga"
EndSection

Section "Monitor"
    Identifier  "lvds"
    Option  "PreferredMode" "1440x900"
EndSection

Section "Monitor"
    Identifier  "vga"
    Option  "PreferredMode" "1280x1024"
    Option  "Position"  "0 0"
EndSection
```


Currently, I have to disactivate the laptop screen every time (using a randr frontend).

TIA,

Erik

---

### Post by gordintoronto on 2010-08-03
I'm not aware of xorg.conf allowing conditional statements.

Many laptops have a key combination which rotates among: built-in, external, both. Typically it's Fn-F2 or Fn-F4

---

