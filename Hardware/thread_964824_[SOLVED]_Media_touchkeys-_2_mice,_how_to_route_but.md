---
title: "[SOLVED] Media touchkeys- 2 mice, how to route button events differently?"
date: 2008-10-31
forum: Hardware
---

### Post by FokkerCharlie on 2008-10-31
Hi All

I have an Acer Aspire 5920G which works well, in general, with Ubuntu.  It was working very nicely indeed with HH, but I couldn't resist having a fiddle, and have upgraded to II.  There are a few snags, which I mention here:

[http://ubuntuforums.org/showthread.php?p=6067640#post6067640]("http://ubuntuforums.org/showthread.php?p=6067640#post6067640")

I'd like to ask here about the media keys.  On the RHS of the keyboard, are four illuminated touch-sensitive buttons.  They are, in fact, recognised by evdev (I think) as another touchpad.  So cat /proc/bus/input/devices returns 2 touchpads:


```
I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio3/input0
S: Sysfs=/devices/platform/i8042/serio3/input/input9
U: Uniq=
H: Handlers=mouse2 event9 
B: EV=b
B: KEY=6420 0 7001f 0 0 0 0 0 0 0 0
B: ABS=11000003
```

and:

```
I: Bus=0011 Vendor=0002 Product=0007 Version=81b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio4/input0
S: Sysfs=/devices/platform/i8042/serio4/input/input11
U: Uniq=
H: Handlers=mouse3 event11 
B: EV=b
B: KEY=6420 0 7000f 0 0 0 0 0 0 0 0
B: ABS=11000003
```

That's all very well, but the touchkeys are reported by xev as buttons 4,5,6,7; so using xbindkeys (as we have been doing in HH) means that using the 2-axis scroll button on the proper touchpad manipulates the media player!  That's no good.

xev output from pressing a media (play/pause) key:

```
EnterNotify event, serial 32, synthetic NO, window 0x3e00001,
    root 0x13b, subw 0x0, time 2087588, (27,45), root:(547,93),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 2048

KeymapNotify event, serial 32, synthetic NO, window 0x0,
    keys:  59  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

LeaveNotify event, serial 32, synthetic NO, window 0x3e00001,
    root 0x13b, subw 0x0, time 2087588, (27,45), root:(547,93),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 2048

ButtonPress event, serial 32, synthetic NO, window 0x3e00001,
    root 0x13b, subw 0x3e00002, time 2087588, (27,45), root:(547,93),
    state 0x0, button 4, same_screen YES

EnterNotify event, serial 32, synthetic NO, window 0x3e00001,
    root 0x13b, subw 0x0, time 2087588, (27,45), root:(547,93),
    mode NotifyGrab, detail NotifyInferior, same_screen YES,
    focus YES, state 2048

KeymapNotify event, serial 32, synthetic NO, window 0x0,
    keys:  59  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

ButtonRelease event, serial 32, synthetic NO, window 0x3e00001,
    root 0x13b, subw 0x3e00002, time 2087638, (27,45), root:(547,93),
    state 0x800, button 4, same_screen YES

LeaveNotify event, serial 32, synthetic NO, window 0x3e00001,
    root 0x13b, subw 0x0, time 2087638, (27,45), root:(547,93),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0
```

The previous method for getting the buttons to work properly are described at the start of the [aforementioned thread]("http://ubuntuforums.org/showthread.php?t=911184").  However, as xorg.conf seems to have gone out of fashion, this no longer works.

Essentially, we need a method of getting xbindkeys to map key presses from only one touchpad and not the other, or to remap the buttons on the media keys 'touchpad'.  Or something else, that I don't know of!

As an aside, the touchpad now works without any tweaking, and my Trackman works better, too.  So we wins on the swings...

Your advice is greatly appreciated.

Charlie

---

### Post by FokkerCharlie on 2008-11-04
Fix found - see post #34

[http://ubuntuforums.org/showthread.php?t=911184&page=4]("http://ubuntuforums.org/showthread.php?t=911184&page=4")

The key is:

xinput set-button-map

Charlie

Charlie

---

