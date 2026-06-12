---
title: "touchscreen drivers for pioneer dreambook"
date: 2010-04-16
forum: Hardware
---

### Post by scott__ on 2010-04-16
hi,

ive had this dreambook (TN121R) from the australian company pioneer ([http://www.pioneercomputers.com.au]("http://www.pioneercomputers.com.au")) for a couple of years now and ive only just switched over from windows to ubuntu. The touchscreen does not work in ubuntu and i have no idea what brand it is.

Ive read a couple of other similar posts and ran 
more /proc/bus/input/devices | grep -F Name
and got
N: Name="Power Button"
N: Name="Power Button"
N: Name="Sleep Button"
N: Name="Lid Switch"
N: Name="Macintosh mouse button emulation"
N: Name="AT Translated Set 2 keyboard"
N: Name="Video Bus"
N: Name="HDA Digital PCBeep"
N: Name="SynPS/2 Synaptics TouchPad"
so not useful.

The only other information i know is that running
sudo cat /dev/usb/hiddev0
is responsive to the touchscreen.

I would really like to get it working! Any help
would be much appreciated.
--scott

---

### Post by scott__ on 2010-06-20
ive made further progress on this problem, but its taken months!

ive found my touchscreen to be a MagicTouch.

and there appear to be drivers available in previous versions of ubuntu ([http://packages.ubuntu.com/source/hardy/xserver-xorg-input-magictouch](http://packages.ubuntu.com/source/hardy/xserver-xorg-input-magictouch)),  but not in 10.04 that im using atm. Is there any reason why this package no longer exists?

Thanks for any help
--scott

---

