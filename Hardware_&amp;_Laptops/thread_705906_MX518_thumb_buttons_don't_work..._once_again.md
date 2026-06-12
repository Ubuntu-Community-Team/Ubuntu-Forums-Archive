---
title: "MX518 thumb buttons don't work... once again"
date: 2008-02-23
forum: Hardware &amp; Laptops
---

### Post by u_roland on 2008-02-23
Hi there,

I switched to Ubuntu a couple of weeks ago and I am more than happy with it. These forums are a great help. :) Yet still some problems do remain :( and here is one of them.

I'm sorry to bring this up again, there are like hundreds of posts concerning my problem:
I don't get my thumb buttons to work :( I googled and I looked through this forum and tried dozens of configs, but I just can't get it to work.

I run Kubuntu 7.10. My MX518 works fine, the main buttons do their job, so does the mousewheel, just the side buttons don't do anything and don't seem to be recognized at all. 

There is no xev output when I press one of them: (pressed: left, right, mousewheel, mousewheel up, mousewheel down, forward thumb, backward thumb, inc res, dec res, task)

```
KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  4294967175 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ConfigureNotify event, serial 31, synthetic YES, window 0x3200001,
    event 0x3200001, window 0x3200001, (909,385), width 178, height 178,
    border_width 2, above 0x1e00d96, override NO

ButtonRelease event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x3200002, time 1227199682, (17,46), root:(928,433),
    state 0x110, button 1, same_screen YES

LeaveNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227199682, (17,46), root:(928,433),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

EnterNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227200042, (17,46), root:(928,433),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 1040

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  4294967175 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ConfigureNotify event, serial 31, synthetic NO, window 0x3200001,
    event 0x3200001, window 0x3200001, (909,385), width 178, height 178,
    border_width 2, above 0x3400007, override NO

ConfigureNotify event, serial 31, synthetic YES, window 0x3200001,
    event 0x3200001, window 0x3200001, (909,385), width 178, height 178,
    border_width 2, above 0x1e00d96, override NO

LeaveNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227200043, (17,46), root:(928,433),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 1040

ButtonPress event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x3200002, time 1227200042, (17,46), root:(928,433),
    state 0x10, button 3, same_screen YES

EnterNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227200043, (17,46), root:(928,433),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 1040

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ConfigureNotify event, serial 31, synthetic YES, window 0x3200001,
    event 0x3200001, window 0x3200001, (909,385), width 178, height 178,
    border_width 2, above 0x1e00d96, override NO

ButtonRelease event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x3200002, time 1227200146, (17,46), root:(928,433),
    state 0x410, button 3, same_screen YES

LeaveNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227200146, (17,46), root:(928,433),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

EnterNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227200834, (17,46), root:(928,433),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 528

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  4294967175 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ConfigureNotify event, serial 31, synthetic NO, window 0x3200001,
    event 0x3200001, window 0x3200001, (909,385), width 178, height 178,
    border_width 2, above 0x3400007, override NO

ConfigureNotify event, serial 31, synthetic YES, window 0x3200001,
    event 0x3200001, window 0x3200001, (909,385), width 178, height 178,
    border_width 2, above 0x1e00d96, override NO

LeaveNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227200835, (17,46), root:(928,433),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 528

ButtonPress event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x3200002, time 1227200834, (17,46), root:(928,433),
    state 0x10, button 2, same_screen YES

EnterNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227200835, (17,46), root:(928,433),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 528

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ConfigureNotify event, serial 31, synthetic YES, window 0x3200001,
    event 0x3200001, window 0x3200001, (909,385), width 178, height 178,
    border_width 2, above 0x1e00d96, override NO

ButtonRelease event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x3200002, time 1227201010, (17,46), root:(928,433),
    state 0x210, button 2, same_screen YES

LeaveNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227201010, (17,46), root:(928,433),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

MotionNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x3200002, time 1227201058, (16,46), root:(927,433),
    state 0x10, is_hint 0, same_screen YES

EnterNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227201810, (16,46), root:(927,433),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 2064

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  4294967175 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

LeaveNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227201810, (16,46), root:(927,433),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 2064

ButtonPress event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x3200002, time 1227201810, (16,46), root:(927,433),
    state 0x10, button 4, same_screen YES

EnterNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227201810, (16,46), root:(927,433),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 2064

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  4294967175 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ButtonRelease event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x3200002, time 1227201810, (16,46), root:(927,433),
    state 0x810, button 4, same_screen YES

LeaveNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227201810, (16,46), root:(927,433),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

EnterNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227202730, (16,46), root:(927,433),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 4112

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  4294967175 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

LeaveNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227202730, (16,46), root:(927,433),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 4112

ButtonPress event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x3200002, time 1227202730, (16,46), root:(927,433),
    state 0x10, button 5, same_screen YES

EnterNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227202730, (16,46), root:(927,433),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 4112

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  4294967175 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ButtonRelease event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x3200002, time 1227202730, (16,46), root:(927,433),
    state 0x1010, button 5, same_screen YES

LeaveNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227202730, (16,46), root:(927,433),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 16

MotionNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x3200002, time 1227205697, (16,45), root:(927,432),
    state 0x10, is_hint 0, same_screen YES

EnterNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227207577, (4,43), root:(915,430),
    mode NotifyNormal, detail NotifyInferior, same_screen YES,
    focus YES, state 16

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  4294967175 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

LeaveNotify event, serial 31, synthetic NO, window 0x3200001,
    root 0x187, subw 0x0, time 1227207585, (-24,43), root:(887,430),
    mode NotifyNormal, detail NotifyNonlinear, same_screen YES,
    focus YES, state 16

FocusOut event, serial 31, synthetic NO, window 0x3200001,
    mode NotifyNormal, detail NotifyNonlinear

PropertyNotify event, serial 31, synthetic NO, window 0x3200001,
    atom 0x19f (_NET_WINDOW_DECOR), time 1227212746, state PropertyNewValue

PropertyNotify event, serial 31, synthetic NO, window 0x3200001,
    atom 0x1a0 (_COMPIZ_WM_WINDOW_BLUR_DECOR), time 1227212754, state PropertyNewValue

```

here is what cat /proc/bus/input/devices says:

```
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
U: Uniq=
H: Handlers=mouse0 event0
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
U: Uniq=
H: Handlers=kbd event1
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=046d Product=c051 Version=0110
N: Name="Logitech USB-PS/2 Optical Mouse"
P: Phys=usb-0000:00:02.0-2/input0
S: Sysfs=/class/input/input2
U: Uniq=
H: Handlers=mouse1 event2
B: EV=7
B: KEY=ff0000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input3
U: Uniq=
H: Handlers=kbd event3
B: EV=40001
B: SND=6

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=button_power/button/input0
S: Sysfs=/class/input/input4
U: Uniq=
H: Handlers=kbd event4
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input5
U: Uniq=
H: Handlers=kbd event5
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0006 Vendor=001f Product=001f Version=0000
N: Name="Mouseemu virtual keyboard"
P: Phys=
S: Sysfs=/class/input/input6
U: Uniq=
H: Handlers=kbd event6
B: EV=100003
B: KEY=1ffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff ffffffff

I: Bus=0006 Vendor=001f Product=001e Version=0000
N: Name="Mouseemu virtual mouse"
P: Phys=
S: Sysfs=/class/input/input7
U: Uniq=
H: Handlers=mouse2 event7
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103
```

my current xorg.conf entry looks like this:

```

#Section "InputDevice"
#       Identifier    "Configured Mouse"
#       Driver        "mouse"
#	Option        "Protocol"       "evdev"
#	Option        "Dev Name"    "Logitech USB-PS/2 Optical Mouse"
#    	Option        "Dev Phys"     "usb-0000:00:02.0-2/input0" 
#       Option        "Device"         "/dev/input/event2"
#    	Option        "Buttons"        "10"
#    	Option        "ZAxisMapping"   "4 5"
#EndSection

#Section "InputDevice"
#        Identifier   "Configured Mouse"
#        Driver      "evdev"
#	 Option	     "Core Pointer"
#        Option      "Name"   "Logitech USB-PS/2 Optical Mouse"
#EndSection

Section "InputDevice"
        Identifier   "Configured Mouse"
        Driver      "evdev"
        Option      "Name"   "Logitech USB-PS/2 Optical Mouse"
        Option      "Buttons"       "7"
        Option      "ZAxisMapping"  "4 5"
        Option      "ButtonMapping" "1 2 3 6 7"
EndSection

```

I've got the first one from one of the guides (the last one I tried). With it I cant get into the GUI. With the second one I get into the GUI but the cursor is frozen.

This is the output of lomoco -s:

```
003.001: 0000:0000 Not a Logitech device
002.001: 0000:0000 Not a Logitech device
001.004: 046d:c051 Unsupported Logitech device: Unknown
001.003: 6547:0232 Not a Logitech device
001.001: 0000:0000 Not a Logitech device

```

I had btnx installed. It didn't react to the thumb buttons when I tried to detect them. So I uninstalled it.

I used the setpoint software under windows on the same desktop, and it didn't work either.
Yet if I plug the MX518 into my laptop(boot windows XP with setpoint) it works perfectly including the thumb buttons. Same thing with that laptop(boot ubuntu 7.10).

I also tried an MX510 on the desktop(windows/setpoint) and the laptop(ubuntu or windows/setpoint) and it worked fine. 

I'll gladly provide any further information you need to solve this!
Thanks in advance :)

---

### Post by zodwallop on 2008-02-23
I just installed Ubuntu earlier today and followed this short tutorial:
[http://asusg1s.wikidot.com/ubuntu-7-10#toc13](http://asusg1s.wikidot.com/ubuntu-7-10#toc13)
And it did the trick for me.  The side buttons were up and running in under five minutes.  Hope it works for you!

---

### Post by u_roland on 2008-02-24
Thanks for the quick answer. :) I tried that guide and changed the xorg.conf accordingly. The thumb buttons still don't work though.:(

---

