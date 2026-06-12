---
title: "xp-pen g430 - ubuntu 18.04 wayland"
date: 2019-08-12
forum: Hardware
---

### Post by juanh5 on 2019-08-12
i have a xp-pen g430 graphic tablet, the vendor drivers never worked for me but recently discovered that in **ubuntu 18.04 wayland** the tablet was somehow recognized and, finally, usable with the digimend driver ([https://github.com/DIGImend/digimend-kernel-drivers/releases/tag/v9]("https://github.com/DIGImend/digimend-kernel-drivers/releases/tag/v9")).
The problem is that in krita or gimp, the pointer becomes independent to the mouse, and disappears when outside the canvas, which makes it hard to select another tool, etc. The mouse can be used for this, but is somehow overrided by the stylus, so nothing can be selected with the mouse until you touch something outside the program window...


in /usr/share/X11/xorg.conf.d/50-digimend.conf i have:

```
#
# InputClass sections for some tablets supported by the DIGImend kernel
# drivers. Organized into separate InputClass sections based on (one of) the
# advertised brands. Mostly because the MatchUSBID options would become too
# long otherwise.
#
Section "InputClass"
	Identifier "Huion tablets with Wacom driver"
	MatchUSBID "5543:006e|256c:006e"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Ugee/XP-Pen tablets with Wacom driver"
	MatchUSBID "28bd:007[145]|28bd:0094|28bd:0042|5543:004[57]|5543:0081|5543:0004|5543:3031"
	# Exclude the original WP5540U which PID is reused by Ugee M540
	NoMatchProduct "MousePen"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Ugtizer tablets with Wacom driver"
	MatchUSBID "2179:0053"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection

Section "InputClass"
	Identifier "Yiynova tablets with Wacom driver"
	MatchUSBID "5543:004d"
	MatchDevicePath "/dev/input/event*"
	Driver "wacom"
EndSection


```
my tablet is in 28bd:007, but the command ```
xsetwacom --list devices
``` ouputs nothing

---

