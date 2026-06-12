---
title: "Slim Tablet on Intrepid"
date: 2008-11-01
forum: Hardware
---

### Post by antario91 on 2008-11-01
I have a problem with my Aiptek Slim Tablet on Ubuntu Intrepid Ibex.
It WORKED fine on Hardy after a series of setups.
I have made a udev rule for the tablet:
```
BUS=="usb", KERNEL=="event[0-9]*", SYSFS{idVendor}=="172f", \
        SYMLINK+="input/slim", OWNER="root", MODE="0666"
```
And I configured my xorg.conf:
```
Section "ServerLayout"
	Identifier     "aticonfig Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	Inputdevice	"tablet" "SendCoreEvents"
EndSection

Section "InputDevice"
         Identifier "tablet"
         Driver "wacom"
         Option "Device" "/dev/input/slim"
         Option "Type"   "stylus"
  	  Option "PressCurve" 	"25,0,100,75"
         Option "USB"    "on"
         Option  "TopX"          "0"
         Option  "TopY"          "0"
         Option  "BottomX"       "10000"
         Option  "BottomY"       "6250"
         Option  "MaxX"          "10000"
         Option  "MaxY"          "6250"
EndSection
```
And Still it does not work... The mouse positioning (absolute) works fine, but when i try to click (by pressing on the tablet) the mouse freezes. I have to lift the pen, then I can move the mouse again, but can not click!
Help would be greatly appreciated.
Thanks in advance, Antario.

---

