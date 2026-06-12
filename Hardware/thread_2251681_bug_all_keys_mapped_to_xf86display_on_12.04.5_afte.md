---
title: "bug: all keys mapped to xf86display on 12.04.5 after suspend"
date: 2014-11-06
forum: Hardware
---

### Post by roelanddilz on 2014-11-06
Since I've updated from 12.04.1 to 12.04.5 the following bug is bothering me:

I don't know what exactly triggers this, but I think it has to do with suspend/resume and/or the change of resolution of the screen.
After a reboot the system works fine. (set up: laptop HP840; WM: fvwm-crystal; docking station with extra monitor; use of open source intel driver for X)
When I suspend my system take it from the docking station and then resume it, this bug might be triggered (not completely sure of this).

The bug was first noticed by a flickering of the screen in many applications. After some research I found out with xev that whenever I press a key on the notebook keyboard, there is also an output of xf86display


xev output for one keypress 'g'
```

KeyPress event, serial 35, synthetic NO, window 0xe00001,
    root 0xc2, subw 0x0, time 71467912, (169,174), root:(1641,230),
    state 0x2000, keycode 235 (keysym 0x1008ff59, XF86Display), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0xe00001,
    root 0xc2, subw 0x0, time 71467912, (169,174), root:(1641,230),
    state 0x2000, keycode 235 (keysym 0x1008ff59, XF86Display), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 35, synthetic NO, window 0xe00001,
    root 0xc2, subw 0x0, time 71467912, (169,174), root:(1641,230),
    state 0x2000, keycode 235 (keysym 0x1008ff59, XF86Display), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0xe00001,
    root 0xc2, subw 0x0, time 71467912, (169,174), root:(1641,230),
    state 0x2000, keycode 235 (keysym 0x1008ff59, XF86Display), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 35, synthetic NO, window 0xe00001,
    root 0xc2, subw 0x0, time 71467912, (169,174), root:(1641,230),
    state 0x2000, keycode 42 (keysym 0x67, g), same_screen YES,
    XLookupString gives 1 bytes: (67) "g"
    XmbLookupString gives 1 bytes: (67) "g"
    XFilterEvent returns: False

KeyPress event, serial 35, synthetic NO, window 0xe00001,
    root 0xc2, subw 0x0, time 71467984, (169,174), root:(1641,230),
    state 0x2000, keycode 235 (keysym 0x1008ff59, XF86Display), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0xe00001,
    root 0xc2, subw 0x0, time 71467984, (169,174), root:(1641,230),
    state 0x2000, keycode 235 (keysym 0x1008ff59, XF86Display), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0xe00001,
    root 0xc2, subw 0x0, time 71467984, (169,174), root:(1641,230),
    state 0x2000, keycode 42 (keysym 0x67, g), same_screen YES,
    XLookupString gives 1 bytes: (67) "g"
    XFilterEvent returns: False

```


Since gnome-settings-daemon reacts to this xf86display-key by redrawing all windows, typing will become quite difficult. The computer becomes largely useless.
The faulty behaviour is also present in virtual terminal mode (ctrl-alt-f1) making it impossible to login, since I cannot insert a password.

For graphical sessions I can kill gnome-settings daemon as a partial workaround. This will make the computer usable, but pressing a key for a long time will not trigger a repetition of the key (since it is seen as a repetition of xf86display key instead of the key I want). This is still quite annoying.

Another workaround is to connect an external keyboard, since an external keyboard will normally not be bothered by the bug. (although sometimes it is)




Is there any way to "reset" the keyboard behaviour? Reload modules? (which is hard to do without any keyboard) 
It seems the bug is present on a low level: I think it is on a lower level than X.
Should I file an official bug report?

---

