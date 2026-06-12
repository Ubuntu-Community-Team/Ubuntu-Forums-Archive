---
title: "Erratic keyboard behavior"
date: 2020-06-11
forum: Hardware
---

### Post by ricardo-pedri on 2020-06-11
Hello people,
I have an Asus laptop with Ubuntu installed.
Recently my Super key (the one with the Windows icon) stopped working.
Another thing that may be related: I use the keyboard in Accessibility mode, to use the keyboard as if it were the mouse. However, when pressing key 5, which should generate a left click, a right click is being generated in turn.

---

### Post by lvm on 2020-06-13
My first guess would be a hardware issue. Run xev to check

---

### Post by ricardo-pedri on 2020-06-13
> **lvm said:**
> My first guess would be a hardware issue. Run xev to check

I thought so, like a stuck key right?
But when I use XEV, it doesn't seem to indicate that.

Here's XEV output, after running it and pressing CTRL+C right afterwards:

```
Outer window is 0x5e00001, inner window is 0x5e00002

PropertyNotify event, serial 8, synthetic NO, window 0x5e00001,
    atom 0x27 (WM_NAME), time 618720, state PropertyNewValue

PropertyNotify event, serial 9, synthetic NO, window 0x5e00001,
    atom 0x22 (WM_COMMAND), time 618720, state PropertyNewValue

PropertyNotify event, serial 10, synthetic NO, window 0x5e00001,
    atom 0x28 (WM_NORMAL_HINTS), time 618720, state PropertyNewValue

CreateNotify event, serial 11, synthetic NO, window 0x5e00001,
    parent 0x5e00001, window 0x5e00002, (10,10), width 50, height 50
border_width 4, override NO

PropertyNotify event, serial 14, synthetic NO, window 0x5e00001,
    atom 0x16f (WM_PROTOCOLS), time 618720, state PropertyNewValue

MapNotify event, serial 15, synthetic NO, window 0x5e00001,
    event 0x5e00001, window 0x5e00002, override NO

PropertyNotify event, serial 18, synthetic NO, window 0x5e00001,
    atom 0x17d (_NET_WM_STATE), time 618721, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x5e00001,
    atom 0x177 (_NET_WM_DESKTOP), time 618721, state PropertyNewValue

ConfigureNotify event, serial 18, synthetic NO, window 0x5e00001,
    event 0x5e00001, window 0x5e00001, (0,0), width 178, height 178,
    border_width 0, above 0x6000009, override NO

ReparentNotify event, serial 18, synthetic NO, window 0x5e00001,
    event 0x5e00001, window 0x5e00001, parent 0x817804,
    (1,32), override NO

ConfigureNotify event, serial 18, synthetic NO, window 0x5e00001,
    event 0x5e00001, window 0x5e00001, (1,32), width 178, height 178,
    border_width 0, above 0x817813, override NO

ConfigureNotify event, serial 18, synthetic YES, window 0x5e00001,
    event 0x5e00001, window 0x5e00001, (871,479), width 178, height 178,
    border_width 0, above 0x0, override NO

MapNotify event, serial 18, synthetic NO, window 0x5e00001,
    event 0x5e00001, window 0x5e00001, override NO

VisibilityNotify event, serial 18, synthetic NO, window 0x5e00001,
    state VisibilityUnobscured

Expose event, serial 18, synthetic NO, window 0x5e00001,
    (0,0), width 178, height 10, count 3

Expose event, serial 18, synthetic NO, window 0x5e00001,
    (0,10), width 10, height 58, count 2

Expose event, serial 18, synthetic NO, window 0x5e00001,
    (68,10), width 110, height 58, count 1

Expose event, serial 18, synthetic NO, window 0x5e00001,
    (0,68), width 178, height 110, count 0

PropertyNotify event, serial 18, synthetic NO, window 0x5e00001,
    atom 0x1a0 (WM_STATE), time 618724, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x5e00001,
    atom 0x1d3 (_NET_WM_ALLOWED_ACTIONS), time 618724, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x5e00001,
    atom 0x17d (_NET_WM_STATE), time 618724, state PropertyNewValue

FocusIn event, serial 18, synthetic NO, window 0x5e00001,
    mode NotifyNormal, detail NotifyNonlinear

KeymapNotify event, serial 18, synthetic NO, window 0x0,
    keys:  4294967237 0   0   0   16  0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

PropertyNotify event, serial 18, synthetic NO, window 0x5e00001,
    atom 0x174 (_NET_FRAME_EXTENTS), time 618725, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x5e00001,
    atom 0x17d (_NET_WM_STATE), time 618725, state PropertyNewValue

PropertyNotify event, serial 18, synthetic NO, window 0x5e00001,
    atom 0x17d (_NET_WM_STATE), time 618725, state PropertyNewValue

PropertyNotify event, serial 33, synthetic NO, window 0x5e00001,
    atom 0x1d6 (_NET_WM_ICON_GEOMETRY), time 618746, state PropertyNewValue

KeyRelease event, serial 34, synthetic NO, window 0x5e00001,
    root 0x191, subw 0x0, time 618772, (426,341), root:(1297,820),
    state 0x0, keycode 36 (keysym 0xff0d, Return), same_screen YES,
"   XLookupString gives 1 bytes: (0d) "
    XFilterEvent returns: False

FocusOut event, serial 37, synthetic NO, window 0x5e00001,
    mode NotifyNormal, detail NotifyNonlinear

PropertyNotify event, serial 37, synthetic NO, window 0x5e00001,
    atom 0x17d (_NET_WM_STATE), time 619502, state PropertyNewValue

```

---

