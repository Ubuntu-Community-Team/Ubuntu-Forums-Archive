---
title: "touchpad does not recognize multitouch"
date: 2010-01-09
forum: Hardware
---

### Post by adamouser on 2010-01-09
hi guys

i have karmic installed on my dell adamo. according to synclient -m 500 the touchpad does not recognize multiple fingers at the same time. ive already tried to activate two finger scroll with system > preferences > mouse. it does not work.

i know the hardware is able to recognize multitouch because its working on windows 7.

what can i do? upgrade synaptics driver?


thanks for your help.

---

### Post by SimonErich on 2010-01-14
I have the same problem with my Toshiba A500.
My Touchpad has multitouch support (I can zoom by spreading my fingers, rotate, ... with this touchpad) but synclient recognizes only one finger.

I would be thankful for your help guys.

thank you.

---

### Post by SeanBlader on 2010-01-29
That would be really cool if we could get this functionality into the touchpad driver, I didn't even know my hardware supported it.

---

### Post by wankel786 on 2010-02-22
Same problem here on an xps 1640. Windows 7 has multitouch but linux does not. Anyone figure this out yet?

---

### Post by adamouser on 2010-05-03
there is a project going on for enabling multitouch etc on macbooks using ubuntu. I am currently following this thread:

[http://ubuntuforums.org/showthread.php?t=1334696](http://ubuntuforums.org/showthread.php?t=1334696)

---

### Post by adamouser on 2010-07-30
IT WORKS

ive received the following hint via the dell-adamo mailing list on launchpad ([https://launchpad.net/~dell-adamo):](https://launchpad.net/~dell-adamo):)


***********

[FONT=Times New Roman]Hi all,[/FONT]
[FONT=Times New Roman]
[/FONT]
[FONT=Times New Roman]New to the list.  Just got my Adamo last week.[/FONT]
[FONT=Times New Roman]
[/FONT]
[FONT=monospace]Just in case anyone is still wondering about this, two finger scrolling is indeed possible on the Adamo.  I'm scrolling right now :-).  I have Lucid installed, but it should work in Karmic as well.[/FONT]
[FONT=monospace]
[/FONT]
[FONT=monospace]Here's what I had to do:[/FONT]
[FONT=monospace]
[/FONT]
[FONT=monospace]Edit the following file;[/FONT]
[FONT=monospace]sudo vi /usr/lib/X11/xorg.conf.d/10-synaptics.conf[/FONT]
[FONT=monospace]
[/FONT]
[FONT=monospace]Add the following three "option" strings in the first block to look like this:[/FONT]
[FONT=monospace]
[/FONT]
[FONT=monospace]Section "InputClass"
        Identifier "touchpad catchall"
        MatchIsTouchpad "on"
        MatchDevicePath "/dev/input/event*"
        Driver "synaptics"
        Option "VertTwoFingerScroll" "true"
        Option "EmulateTwoFingerMinZ"  "10"
        Option "EmulateTwoFingerMinW" "8"
EndSection




Save the file.  This in theory would make two finger scrolling possible, however there is a bug in that the VertTwoFingerScroll option is not honored at startup (pressure and width are honored), so you have to use a work-around.


Create a file in your home directory:
vi ~/.twofingerscroll


Add the following:
#!/bin/bash
sleep 10 &&
exec synclient VertTwoFingerScroll=1 &
exit



Make it executable:
chmod +x ~/.twofingerscroll


Add it to your startup items in System -> Preferences -> Startup Applications


Reboot.


Enjoy two finger goodness :-)


Hope this  helps.


Matthew Percival


PS - You can also add horizontal scrolling if you'd like.  Add the option line to xorg and to the workaround using [HorizTwoFingerScroll].
[/FONT]
[FONT=Times New Roman]
[/FONT]

---

### Post by Ole_M on 2010-08-21
> **adamouser said:**
> [FONT=monospace]
[/FONT][FONT=monospace]however there is a bug in that the VertTwoFingerScroll option is not honored at startup[/FONT][FONT=Times New Roman]
[/FONT]

Hm, for me it works just fine. I use openbox as a window manager. Maybe it has something to do with gnome? By the way, horizontal scrolling also flips through desktops 1-4. Nice! Additionally, a two-finger-tap emulates the right mouse button.

Is there the possibility to add more multitouch functionality, e.g. pinching or recognizing 3 finger tabs/scrolls?

Ole

---

