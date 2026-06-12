---
title: "Air mouse problems"
date: 2020-01-03
forum: Hardware
---

### Post by Alexander_Lilljebj on 2020-01-03
Hey,
I've been googling and searching quite alot, but still haven't found a solution for this.
I've gotten myself a no name air mouse off of ebay.
I'm running Ubuntu Mate 18.04 x64 as a media center pc(not laptop).
[ATTACH=CONFIG]284736[/ATTACH]

It kind of works, but it seems it's continuously scrolling or edge scrolling. so it's not really usable atm. 
I thought I would disable scrolling all together to see if that made any difference, but I can't even find how to accomplish that(!).

```

media@media:~$ xinput
\u23a1 Virtual core pointer                        id=2    [master pointer  (3)]
\u239c   \u21b3 Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
\u239c   \u21b3 Adafruit Trinket HID Combo Mouse            id=12    [slave  pointer  (2)]
\u239c   \u21b3 Adafruit Trinket HID Combo Consumer Control    id=14    [slave  pointer  (2)]
\u239c   \u21b3 Usb Composite Device Usb Composite Device Consumer Control    id=18    [slave  pointer  (2)]
\u239c   \u21b3 Usb Composite Device Usb Composite Device Mouse    id=21    [slave  pointer  (2)]
\u23a3 Virtual core keyboard                       id=3    [master keyboard (2)]
    \u21b3 Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    \u21b3 Power Button                                id=6    [slave  keyboard (3)]
    \u21b3 Video Bus                                   id=7    [slave  keyboard (3)]
    \u21b3 Power Button                                id=8    [slave  keyboard (3)]
    \u21b3 Sleep Button                                id=9    [slave  keyboard (3)]
    \u21b3 Adafruit Trinket HID Combo Keyboard         id=13    [slave  keyboard (3)]
    \u21b3 Adafruit Trinket HID Combo System Control    id=15    [slave  keyboard (3)]
    \u21b3 Eee PC WMI hotkeys                          id=16    [slave  keyboard (3)]
    \u21b3 AT Translated Set 2 keyboard                id=17    [slave  keyboard (3)]
    \u21b3 Adafruit Trinket HID Combo Consumer Control    id=19    [slave  keyboard (3)]
    \u21b3 Usb Composite Device Usb Composite Device    id=10    [slave  keyboard (3)]
    \u21b3 Usb Composite Device Usb Composite Device System Control    id=11    [slave  keyboard (3)]
    \u21b3 Usb Composite Device Usb Composite Device Consumer Control    id=20    [slave  keyboard (3)]
``` 

```

media@media:~$ lsusb
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1781:24ab Multiple Vendors 
Bus 001 Device 006: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 001 Device 007: ID 2319:0014  
Bus 001 Device 002: ID 2001:3318 D-Link Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

I have no idea where to start. Tried looking for xorg.conf, but couldn't find it in the usual places.
Does anyone have any ideas how to change this behavior?

Thanks for reading.

Edit:
It seems that id 10, 11 and 20 are the remote. I tried disabling all scroll this way but it doesn't seem to do anything.

```
media@media:~$ xinput list 10Usb Composite Device Usb Composite Device Consumer Control    id=10    [slave  pointer  (2)]
    Reporting 7 classes:
        Class originated from: 10. Type: XIButtonClass
        Buttons supported: 7
        Button labels: "Button Left" "Button Middle" "Button Right" "Button Wheel Up" "Button Wheel Down" "Button Horiz Wheel Left" "Button Horiz Wheel Right"
        Button state:
        Class originated from: 10. Type: XIValuatorClass
        Detail for Valuator 0:
          Label: Rel X
          Range: -1.000000 - -1.000000
          Resolution: 0 units/m
          Mode: relative
        Class originated from: 10. Type: XIValuatorClass
        Detail for Valuator 1:
          Label: Rel Y
          Range: -1.000000 - -1.000000
          Resolution: 0 units/m
          Mode: relative
        Class originated from: 10. Type: XIValuatorClass
        Detail for Valuator 2:
          Label: Rel Horiz Scroll
          Range: -1.000000 - -1.000000
          Resolution: 0 units/m
          Mode: relative
        Class originated from: 10. Type: XIValuatorClass
        Detail for Valuator 3:
          Label: Rel Vert Scroll
          Range: -1.000000 - -1.000000
          Resolution: 0 units/m
          Mode: relative
        Class originated from: 10. Type: XIScrollClass
        Scroll info for Valuator 2
          type: 2 (horizontal)
          increment: 15.000000
          flags: 0x0
        Class originated from: 10. Type: XIScrollClass
        Scroll info for Valuator 3
          type: 1 (vertical)
          increment: 15.000000
          flags: 0x0


media@media:~$ xinput set-button-map 10 1 0 3 0 0 0 0

```
From here: [https://askubuntu.com/questions/59128/how-to-disable-mouse-wheel-scroll-in-ubuntu-11-04-or-10-10](https://askubuntu.com/questions/59128/how-to-disable-mouse-wheel-scroll-in-ubuntu-11-04-or-10-10)
I know it's old, but it's the only turtorial I've found so far.

The mouse is still making the window it resides in jerk up and down(scrolling) very fast, it's just jumping between "home" and "end" in the window.

---

### Post by Alexander_Lilljebj on 2020-01-08
Alright, the only thing I've figured out is that it isn't scrolling, it's clicking the buttons many many times when moving the mouse cursor (xev | grep ButtonPress, spams the terminal window and hangs).
Anyone know how to fix that?

Thanks.


Edit: Like this, but more times than I can count.
```
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
ButtonPress event, serial 68, synthetic NO, window 0x2e00001,
```

Edit2:
It works in Windows, uses the usbccgp.sys driver.

Edit3: And this in syslog

```
Jan  8 13:04:10 alex-LIFEBOOK gnome-shell[1312]: Window manager warning: Overwriting existing binding of keysym 38 with keysym 38 (keycode 11).
Jan  8 13:04:10 alex-LIFEBOOK gnome-shell[1312]: Window manager warning: Overwriting existing binding of keysym 39 with keysym 39 (keycode 12).
Jan  8 13:04:10 alex-LIFEBOOK gnome-shell[1312]: Window manager warning: Overwriting existing binding of keysym 32 with keysym 32 (keycode b).
Jan  8 13:04:10 alex-LIFEBOOK gnome-shell[1312]: Window manager warning: Overwriting existing binding of keysym 33 with keysym 33 (keycode c).
Jan  8 13:04:10 alex-LIFEBOOK gnome-shell[1312]: Window manager warning: Overwriting existing binding of keysym 34 with keysym 34 (keycode d).
Jan  8 13:04:10 alex-LIFEBOOK gnome-shell[1312]: Window manager warning: Overwriting existing binding of keysym 35 with keysym 35 (keycode e).
Jan  8 13:04:10 alex-LIFEBOOK gnome-shell[1312]: Window manager warning: Overwriting existing binding of keysym 36 with keysym 36 (keycode f).
Jan  8 13:04:10 alex-LIFEBOOK gnome-shell[1312]: Window manager warning: Overwriting existing binding of keysym 37 with keysym 37 (keycode 10).



```

Edit4: And xev looks like this. Scrolls by really fast. And not when moving in the xev window, only in the terminal window.

```
EnterNotify event, serial 34, synthetic NO, window 0x1200001,    
root 0x2ac, subw 0x0, time 376643, (175,63), root:(430,635),
    mode NotifyNormal, detail NotifyAncestor, same_screen YES,
    focus YES, state 16


KeymapNotify event, serial 34, synthetic NO, window 0x0,
    keys:  4294967212 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   


MotionNotify event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376643, (175,63), root:(430,635),
    state 0x10, is_hint 0, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376643, (175,62), root:(430,634),
    state 0x10, button 5, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376643, (175,62), root:(430,634),
    state 0x1010, button 5, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376644, (175,62), root:(430,634),
    state 0x10, button 5, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376644, (175,62), root:(430,634),
    state 0x1010, button 5, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376644, (175,62), root:(430,634),
    state 0x10, button 5, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376644, (175,62), root:(430,634),
    state 0x1010, button 5, same_screen YES


MotionNotify event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376663, (172,53), root:(427,625),
    state 0x10, is_hint 0, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376663, (172,53), root:(427,625),
    state 0x10, button 4, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376663, (172,53), root:(427,625),
    state 0x810, button 4, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376663, (172,53), root:(427,625),
    state 0x10, button 4, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376663, (172,53), root:(427,625),
    state 0x810, button 4, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376663, (172,53), root:(427,625),
    state 0x10, button 5, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376663, (172,53), root:(427,625),
    state 0x1010, button 5, same_screen YES


MotionNotify event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376663, (170,46), root:(425,618),
    state 0x10, is_hint 0, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376663, (170,46), root:(425,618),
    state 0x10, button 4, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376663, (170,46), root:(425,618),
    state 0x810, button 4, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376663, (170,46), root:(425,618),
    state 0x10, button 4, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376663, (170,46), root:(425,618),
    state 0x810, button 4, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376663, (170,46), root:(425,618),
    state 0x10, button 5, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376663, (170,46), root:(425,618),
    state 0x1010, button 5, same_screen YES


MotionNotify event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376680, (165,35), root:(420,607),
    state 0x10, is_hint 0, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376680, (165,35), root:(420,607),
    state 0x10, button 4, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376680, (165,35), root:(420,607),
    state 0x810, button 4, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376680, (165,35), root:(420,607),
    state 0x10, button 4, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376680, (165,35), root:(420,607),
    state 0x810, button 4, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376680, (165,35), root:(420,607),
    state 0x10, button 5, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376680, (165,35), root:(420,607),
    state 0x1010, button 5, same_screen YES


MotionNotify event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376680, (161,24), root:(416,596),
    state 0x10, is_hint 0, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376680, (161,24), root:(416,596),
    state 0x10, button 5, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376680, (161,24), root:(416,596),
    state 0x1010, button 5, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376680, (161,24), root:(416,596),
    state 0x10, button 4, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376680, (161,24), root:(416,596),
    state 0x810, button 4, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376680, (161,24), root:(416,596),
    state 0x10, button 5, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376680, (161,24), root:(416,596),
    state 0x1010, button 5, same_screen YES


MotionNotify event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376696, (157,15), root:(412,587),
    state 0x10, is_hint 0, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376696, (157,15), root:(412,587),
    state 0x10, button 5, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376696, (157,15), root:(412,587),
    state 0x1010, button 5, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376696, (157,15), root:(412,587),
    state 0x10, button 4, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376696, (157,15), root:(412,587),
    state 0x810, button 4, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376696, (157,15), root:(412,587),
    state 0x10, button 5, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376696, (157,15), root:(412,587),
    state 0x1010, button 5, same_screen YES


MotionNotify event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376696, (154,5), root:(409,577),
    state 0x10, is_hint 0, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376696, (154,5), root:(409,577),
    state 0x10, button 5, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376696, (154,5), root:(409,577),
    state 0x1010, button 5, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376696, (154,5), root:(409,577),
    state 0x10, button 4, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376696, (154,5), root:(409,577),
    state 0x810, button 4, same_screen YES


ButtonPress event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376696, (154,5), root:(409,577),
    state 0x10, button 5, same_screen YES


ButtonRelease event, serial 34, synthetic NO, window 0x1200001,
    root 0x2ac, subw 0x0, time 376696, (154,5), root:(409,577),
    state 0x1010, button 5, same_screen YES



```

Anyone pretty please? Even if it's just an idea.

Edit again:

The mouse/remote works as it should on both CentOS/Redhat and OpenSuse, if that helps. But I really don't want to switch just because of this. I hardly have any experience in those OSs.

And again... 
It does not work with Fedora though, gnome or KDE. I'm thinking that there must be another driver alternative. 
Ubuntu registers mouse clicks on movement. I tried disabling all buttons in xinput, but it makes no difference. At this point I wish that it was easier for me to give up...

---

