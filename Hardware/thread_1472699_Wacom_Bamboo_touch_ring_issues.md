---
title: "Wacom Bamboo touch ring issues"
date: 2010-05-04
forum: Hardware
---

### Post by ubootfanat on 2010-05-04
Hi there!

Running Ubuntu 10.04 here on a Dell Latitude E6400. After a clean install, I was surprised to find my Wacom Bamboo (the very first edition with 4 buttons and the tiny scroll wheel at the top) working out of the box. Since HAL is gone I used xsetwacom to configure the tablet like in Gibbon times. Changing twinview options, assigning key strokes, ... all works well. But when it comes to the scroll wheel the system shows strange behavior.

*Challenge*
As soon as I use the scroll wheel, the cursor moves to the top left corner of the screen.

*Findings*
I fondled around and found that every pad button press moves the mouse pointer to the top left corner of the screen if the button is not assigned to a non-mouse button previously. I checked the scroll wheel and set it to button "3" using xsetwacom which results in a correct right click. But guess what, prior to the click, the mouse pointer moves to the top left corner.
I checked the assigned region using xsetwacom get and the topx/y bottomx/y attributes. the result seems to be correct.

*actual issue?*
In fact, whenever the pad triggers a mouse event the mouse cursor moves to the top left corner of the screen (coordinates 0,0).

Any ideas on that one? Any solution? Known issue?

thanks in advance
ubootfanat

*System in detail*
- Ubuntu 10.04
- xserver-xorg-input-wacom 1:0.10.5-0ubuntu4 (tried xf86-input-wacom 10.6, does not work either)
- wacom bamboo [http://www.wacom.eu/bamboo/index.asp?pid=214](http://www.wacom.eu/bamboo/index.asp?pid=214)

---

### Post by Ad1217 on 2010-05-04
I am having the same problem...:(

---

### Post by Diddy on 2010-05-05
I am having the same problems with the Intuos4 pad, also in Gimp no pressure response, all worked perfectly in 9.10.

Being new to Linux I will have to wait until someone comes up with the solution, tried Ubuntu a couple of years ago and gave up because I could not get printers etc working.   Must admit there have been major improvements and I am trying to get to grips with the command line commands etc in the hope I will be able to ditch MS at last.

---

### Post by hazza96 on 2010-09-29
> **Diddy said:**
> I am having the same problems with the Intuos4 pad, also in Gimp no pressure response, all worked perfectly in 9.10.

Being new to Linux I will have to wait until someone comes up with the solution, tried Ubuntu a couple of years ago and gave up because I could not get printers etc working.   Must admit there have been major improvements and I am trying to get to grips with the command line commands etc in the hope I will be able to ditch MS at last.
I could not get the pressure thing in GIMP to work at first, you need to do the following:

[LIST=1][*]Edit / Preferences
[*]Input devices
[*]Configure extened input devices
[*]Select each "Wacom" device in the list and set them to "Screen"
[/LIST]
Now you can have one end of the pen to one tool and the other to a different tool.

I still can't work out how to use the scroll wheel, it still puts the pointer to the top left corner.

---

### Post by erysavy on 2010-12-01
I've been struggling with this for some time now and finally solved it (actually on OpenSuSE 11.3, but I guess this is the same problem caused by an Xorg update):

the touch ring sends motion events with X and Y coordinates being 0. This causes the cursor to move to the absolute position 0,0 which is the top left corner of the screen.

The "pad" device only refers to events from the buttons and the touch ring, therefore we don't need any motion events.

In xorg.conf in the section where the pad is defined I added the option "ButtonsOnly" and turned off SendCoreEvents for the *pad* device, now it works:

> 
Section "InputDevice"[INDENT]    Driver       "wacom"
   Identifier   "pad"
   Option       "Device" "/dev/input/by-id/usb-Wacom_Co._Ltd._MTE-450-mouse"
**   Option       "Type" "pad"**
   Option       "USB" "on"
**Option "SendCoreEvents" "false"**
**   Option       "ButtonsOnly" "on"**
[/INDENT]EndSection
> 
Section "ServerLayout"[INDENT]Identifier   "Layout[all]"
InputDevice  "Keyboard[0]" "CoreKeyboard"
InputDevice  "Mouse[1]" "CorePointer"
InputDevice  "stylus" "SendCoreEvents"
InputDevice  "eraser" "SendCoreEvents"
InputDevice  "cursor" "SendCoreEvents"
**InputDevice  "pad" # omit parameter SendCoreEvents**
[/INDENT]EndSection
The touch ring creates button events as well (like the mouse wheel does) that can be mapped to any action (you can check the button numbers with xev); here it's button 4 and 5 which are the same as the standard mouse scroll wheel events, so scrolling works out of the box.

** Edit:** for some reason, after rebooting the cursor again jumps to the top left corner when using the touch ring or pressing any one of the four buttons.
For the time being the following "workaround" helps at least on my system:

[LIST]
[*]while booting, hold down one of the pad's buttons until the logon screen appears,
[*]or, even if already in X and provided you have root privileges, call *rmmod wacom; sleep 1; modprobe wacom* while (kind of) turning the touch ring before the module gets reloaded.
[/LIST]
I don't see any difference in the log entries between the two cases - working and broken keyring functionality -, the problem might be related to how the kernel module initializes the pad or the module's internal state.

Hope this helps,
Eddie.

---

