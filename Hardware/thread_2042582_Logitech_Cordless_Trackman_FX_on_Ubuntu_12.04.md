---
title: "Logitech Cordless Trackman FX on Ubuntu 12.04"
date: 2012-08-14
forum: Hardware
---

### Post by jwhiz on 2012-08-14
Hi;

I've loved this thing for a long time, and am very used to using it in Windows, especially for typing (I even got the old software working on Windows 7).

I'd like to map the 4 buttons in a very specfic way, but I don't really understand what I've been reading. 

Going from [https://help.ubuntu.com/community/Logitech_Marblemouse_USB/](https://help.ubuntu.com/community/Logitech_Marblemouse_USB/), I tried out some changes in what I think is the config file (11-evdev-trackpoint.conf under /usr/share/X11/xorg.conf.d):

# trackpoint users want wheel emulation
#  Physical buttons come from the mouse as:
    #     Big:   1 3
    #     Small: 8 9
# these refer to big outside buttons and small inside buttons on a Marble, not a trackman FX
# original matchproduct "TrackPoint|DualPoint Stick"

Section "InputClass"
	Identifier	"trackpoint catchall"
	MatchIsPointer	"true"
	MatchProduct	"Logitech USB Receiver"
	MatchDevicePath	"/dev/input/event*"
	Option	"Emulate3Buttons"	"true"
	Option	"EmulateWheel"	"true"
	Option	"EmulateWheelButton"	"2"
	Option	"XAxisMapping"	"6 7"
	Option	"YAxisMapping"	"4 5"
EndSection
(file saved without changes)

what I don't understand are the commands for mapping the buttons.

Here's what the old beast looks like: [http://www.logitech.com/en-us/support/trackballs/960](http://www.logitech.com/en-us/support/trackballs/960)

I'd like to replicate my usual set up for the buttons (the ball is not springloaded, it just moves the cursor).

furthest left, large button -> scroll down (now a regular left click)
middle left button -> regular left click (working now)
upper left button -> double click (currently does I dunno what, and really missing the double click, as this version of Linux requires double clicking on icons!)
right side button -> regular context menu (working now).

Possible the challenge lies more in teaching me how to understand the script than in the actual mapping.:confused:

Otherwise loving 12.04, and managed to dig myself out of a Unity 3D crash earlier today (I really, really want that dock off the side and onto the bottom of the screen!) Unity 2D and Gnome look good and are useful too, Cinnamon not so much (love it in Mint 13). The trackball is not a deal breaker for switching to Ubuntu most of the time from now on but it really saved me some RSI issues. Any suggestions on other wrist-saving pointing devices? I think I also have an old MS thumb trackball, I didn't like using my thumb much, and an old Kensington with the trackball in the middle (like the Logitech Marble).I'm not so keen on touchpads, old or new.Trackball is used currently on Windows side of desktop and on Windows 7 netbook which is going to get something Linux on it soon (Unity does NOT suit tiny screens, I know that much - thinking WUBI with Gnome or dual boot Mint LDME or the XFGE - whatever, one of the two really lightweight desktops. Or stick with virtual player but netbook doesn't have much for resources.)

Ramble ends.

---

### Post by wicking on 2013-02-25
Hi.

Did you manage to assign the buttons as you wanted? How did you do it?

I use the upper left button for scrolling. This button was red at the corded variant of this device called Trackman Marble FX. I did it like in this [http://erikstreb.de/basteln/trackball/](http://erikstreb.de/basteln/trackball/) description, editing the /etc/X11/xorg.conf file.

You can watch the devices output with *xinput*. First list all devices
```
xinput list
```
Search for your Trackman and use its id to watch its output:
```
xinput watch-props 6
```

You could also use *xev* to watch the devices output.

But I don’t know how to remap the keys systemwide. The only way I could imagine is Xmodmap, but I’ve never tried that with a pointing device. And it is only for only user.

---

