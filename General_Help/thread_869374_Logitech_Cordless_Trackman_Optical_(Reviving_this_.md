---
title: "Logitech Cordless Trackman Optical (Reviving this thread)"
date: 2008-07-24
forum: General Help
---

### Post by the real omni on 2008-07-24
Hi,

I use a Logitech Cordless Trackman Optical trackball. 

All the buttons work in FireFox, but in Nautilus and most other apps the back and forward thumb buttons don't work.

I found a lot of threads that explain how to get 5-button mice to work but when I try those configurations it just stops X from loading altogether and I log into a blank screen, so I have to log into a console and revert my xorg.conf.

In the archives I found this thread:
[http://ubuntuforums.org/showthread.php?t=20094]("http://ubuntuforums.org/showthread.php?t=20094")

Unfortunately that person's xorg.conf settings don't work for me. When I use them, X loads but the mouse is frozen in place and I only have keyboard access.

I've also found sites that point to imwheel but after spending an HOUR fiddling with imwheel and not getting any positive results AT ALL it's pretty clear that program is useless with my trackball.

Can anyone explain how to get all the buttons on a Cordless Trackman Optical working properly for all apps?

Thanks! :)

Oh, system specs:
HP Pavillion dv6000 laptop running Ubuntu 8.04 with all of the most current updates installed.

---

### Post by the real omni on 2008-07-24
(bump... forgot to subscribe)

---

### Post by rbmorse on 2008-07-25
in the file /etc/X11/xorg.conf

Under the section "InputDevice" 
	Identifier "Configured Mouse" 

make sure the correct driver is loaded

Option	    "Protocol" "ExplorerPS/2"

then add the lines to the end of the section:

Option "Buttons" "7"
Option "ButtonMapping" "1 2 3 6 7"

---

### Post by the real omni on 2008-07-25
> **rbmorse said:**
> in the file /etc/X11/xorg.conf

Under the section "InputDevice" 
	Identifier "Configured Mouse" 

make sure the correct driver is loaded

Option	    "Protocol" "ExplorerPS/2"

then add the lines to the end of the section:

Option "Buttons" "7"
Option "ButtonMapping" "1 2 3 6 7"

I tried that. With the alterations you proposed, my xorg.conf entry looks like this:

```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Dev Name"              "Logitech USB Receiver"
        Option          "Dev Phys"              "usb*/input0"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/event0"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "7"
	Option		"ButtonMapping"		"1 2 3 6 7"
        Option          "Emulate3Buttons"       "false"
        Option          "ZAxisMapping"          "4 5"
EndSection
```

When I try try to boot using that configuration it takes ages for the login screen to come up and when it finally does, the mouse doesn't move at all. I can log into the desktop and use the keyboard interface, but the only way I can get mouse functionality is to revert back to the default config and re-login.

Is there a conflict in the Section settings or something?

---

### Post by the real omni on 2008-09-28
bump

---

