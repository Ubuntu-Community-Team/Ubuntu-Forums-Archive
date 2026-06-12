---
title: "Wacom Bluetooth mouse clicks work, but no movement"
date: 2010-02-07
forum: Hardware
---

### Post by bakaeigo on 2010-02-07
Hey,

I'm using Karmic and have my Wacom Bluetooth tablet connected via Blueman to my computer. Mouse clicks register fine -- if I press the stylus down on the tablet a mouse click will register. But I can't move the cursor at all with the tablet. What's going on?

---

### Post by Favux on 2010-02-07
Hi bakaeigo,

Not sure what's wrong.  Does your tablet show up in:
```
xinput --list
```
entered in a terminal?

The [Wacom Graphire Bluetooth wiki]("https://help.ubuntu.com/community/WacomGraphireBluetooth") referenced from the [Wacom Graphire Bluetooth thread]("http://ubuntuforums.org/showthread.php?t=674738") says you still need a "tweak".  It sends you to a ppa.

Also you might want to consider the new-generic .fdi at [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").

---

### Post by bakaeigo on 2010-02-07
> **Favux said:**
> Hi bakaeigo,

Not sure what's wrong.  Does your tablet show up in:
```
xinput --list
```
entered in a terminal?

The [Wacom Graphire Bluetooth wiki]("https://help.ubuntu.com/community/WacomGraphireBluetooth") referenced from the [Wacom Graphire Bluetooth thread]("http://ubuntuforums.org/showthread.php?t=674738") says you still need a "tweak".  It sends you to a ppa.

Also you might want to consider the new-generic .fdi at [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176").

I had already previously added the PPA (but its version of bluez is lower than my currently installed version, so the tweak wasn't applied). It did show up in xinput --list, but after I followed the instructions in [post #176]("http://ubuntuforums.org/showpost.php?p=7234134&postcount=176") and restarting, it no longer does, and the mouse click functionality is lost.

---

### Post by Favux on 2010-02-07
It could be something else has your tablet, not linuxwacom.  You could check your Xorg.0.log in /var/log.  Could I see the xinput output with the tablet?  As I understand it the bluetooth module is now in the kernel so:
```
lsmod
```
wouldn't show it.  I guess I'm asking what does the ppa do?  It seems to me I recall the last page or two of the bluetooth thread talking about getting things to work in Karmic.

---

### Post by Reason NL on 2010-02-16
Having the exact same problem. Clicks register, movement does not.
I've also installed blueman from there ppa and it installed version 4.61 of bluez which is way newer than the one found in the proposed fix (4.51) ppa.
All .fdi fixes I tried resulted in loss of all functionality as bakaeigo described.
Turning on the device after pairing and no .fdi fixes results in these entries in the Xorg.0.log:

(II) config/hal: Adding input device WACOM Pen Tablet eraser
(**) WACOM Pen Tablet eraser: always reports core events
(**) WACOM Pen Tablet eraser device is /dev/input/event12
(**) WACOM Pen Tablet eraser is in absolute mode
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) WACOM Pen Tablet eraser: serial speed 9600
(II) XINPUT: Adding extended input device "WACOM Pen Tablet eraser" (type: Wacom Eraser)
(**) Option "Device" "/dev/input/event12"
WACOM Pen Tablet eraser Wacom X driver grabbed event device
(==) Wacom using pressure threshold of 30 for button 1
(==) Wacom USB Graphire4 tablet speed=9600 (38400) maxX=16704 maxY=12064 maxZ=511 resX=2032 resY=2032  tilt=disabled
(==) Wacom device "WACOM Pen Tablet eraser" top X=0 top Y=0 bottom X=16704 bottom Y=12064 resol X=2032 resol Y=2032
(II) config/hal: Adding input device WACOM Pen Tablet cursor
(**) WACOM Pen Tablet cursor: always reports core events
(**) WACOM Pen Tablet cursor device is /dev/input/event12
(**) WACOM Pen Tablet cursor is in relative mode
(**) WACOM: suppress value is 2
(**) WACOM Pen Tablet cursor: reading USB link
(**) WACOM Pen Tablet cursor: threshold = 30
(**) WACOM Pen Tablet cursor: max x set to 16704 by xorg.conf
(**) WACOM Pen Tablet cursor: max y set to 12064 by xorg.conf
(**) WACOM Pen Tablet cursor: max z = 511
(**) Option "BaudRate" "9600"
(**) WACOM Pen Tablet cursor: serial speed 9600
(II) XINPUT: Adding extended input device "WACOM Pen Tablet cursor" (type: Wacom Cursor)
(==) Wacom device "WACOM Pen Tablet cursor" top X=0 top Y=0 bottom X=16704 bottom Y=12064 resol X=2032 resol Y=2032
(II) config/hal: Adding input device WACOM Pen Tablet
(**) WACOM Pen Tablet: always reports core events
(**) WACOM Pen Tablet device is /dev/input/event12
(**) WACOM Pen Tablet is in absolute mode
(**) WACOM: suppress value is 2
(**) WACOM Pen Tablet: reading USB link
(**) WACOM Pen Tablet: threshold = 30
(**) WACOM Pen Tablet: max x set to 16704 by xorg.conf
(**) WACOM Pen Tablet: max y set to 12064 by xorg.conf
(**) WACOM Pen Tablet: max z = 511
(**) Option "BaudRate" "9600"
(**) WACOM Pen Tablet: serial speed 9600
(II) XINPUT: Adding extended input device "WACOM Pen Tablet" (type: Wacom Stylus)
(==) Wacom device "WACOM Pen Tablet" top X=0 top Y=0 bottom X=16704 bottom Y=12064 resol X=2032 resol Y=2032

Moving the pen, pressing the buttons or pressing on the surface of the tablet (with the pen) results in a lot of these entries in the Xorg.0.log:

wacom: rel event recv'd (0)!
wacom: rel event recv'd (1)!
wacom: rel event recv'd (0)!
wacom: rel event recv'd (1)!

But only the pressing on the tablet (and the buttons on the pen itself) results in a response (mouse clicking) nothing else seems to be doing anything.

Searched google for quite some time now, but unfortunately found no fix!

What can I do to fix this?



Related bug report: [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/483453](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/483453)

---

### Post by Reason NL on 2010-03-05
Anyone?

Edit:
Link to howto: [http://ubuntuforums.org/showthread.php?t=674738](http://ubuntuforums.org/showthread.php?t=674738)

---

