---
title: "Toggle FN key"
date: 2012-06-19
forum: Hardware
---

### Post by tuxtm on 2012-06-19
Hi,

A few days ago I have installed Ubuntu 12.04 on a Lenovo ThinkCenter desktop computer at work. The issue I'm facing is that it has a Lenovo USB keyboard for which the multimedia keys (mute, volume up, volume down, record, lock, search etc) have priority against the function keys, meaning that in order to use F1-F12 keys I have to press Fn together with the desired key. 
This computer came with Windows 7 preinstalled and it has an application which allows me to toogle the FN key so I don't have to press it every time I want to use the functional keys.
I tried to get the keycode for the multimedia keys with xev in order to map the muktimedia keys to the function keys with Xmodmap, but I get the following output when I press the mute key (F1 without FN pressed):
```

MappingNotify event, serial 36, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 248

FocusOut event, serial 36, synthetic NO, window 0x3800001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 37, synthetic NO, window 0x3800001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 37, synthetic NO, window 0x3800001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 37, synthetic NO, window 0x0,
    keys:  4294967227 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 
```The only way to get a keycode for the mute key is using showkey:
```

press any key (program terminates 10s after last keypress)...
keycode 113 press
keycode 113 release

```but when I map the keycode 113 to F1 with Xmodmap, nothing changes when I press F1 with Fn key(the volume is (un)muted as before) but it seems that the left arrow key was mapped to f1, because pressing the left arrow key launches the help app. I noticed that the keycode returned with showkey for the left arrow key is 105, but with xev it's 113.
How could I make Ubuntu behave like the Fn key is always pressed(without using duct tape :) )

Thanks,

---

