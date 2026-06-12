---
title: "Compaq V3000 series backlight borked"
date: 2008-08-28
forum: Hardware
---

### Post by aaron552 on 2008-08-28
My backlight control keys stopped working (probably after the last kernel upgrade)
They always used to work (in Ubuntu) but now whenever I try to change the backlight brightness, nothing happens. I've never been able to change the backlight brightness via gnome-powermanager or the brightness applet, but now the keys don't work either.
The keys work in Windows so I know that that's not the problem. xev reports:
"Brightness Down":
```

KeyPress event, serial 31, synthetic NO, window 0x3800001,
    root 0x1a6, subw 0x0, time 2064031, (151,569), root:(156,622),
    state 0x0, keycode 101 (keysym 0x1008ff4d, XF86LaunchD), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3800001,
    root 0x1a6, subw 0x0, time 2064031, (151,569), root:(156,622),
    state 0x0, keycode 101 (keysym 0x1008ff4d, XF86LaunchD), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```
"Brightness Up":
```

KeyPress event, serial 31, synthetic NO, window 0x3800001,
    root 0x1a6, subw 0x0, time 2110166, (505,616), root:(510,669),
    state 0x0, keycode 212 (keysym 0x1008ff4e, XF86LaunchE), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x3800001,
    root 0x1a6, subw 0x0, time 2110166, (505,616), root:(510,669),
    state 0x0, keycode 212 (keysym 0x1008ff4e, XF86LaunchE), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False


```

Any ideas on why it's suddenly stopped working?

---

