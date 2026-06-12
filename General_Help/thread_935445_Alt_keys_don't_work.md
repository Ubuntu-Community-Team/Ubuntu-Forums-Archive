---
title: "Alt keys don't work"
date: 2008-10-01
forum: General Help
---

### Post by sebiolo on 2008-10-01
Until recently, both my alt keys worked fine, but for some reason they don't work anymore. The only exception is left alt+tab, which still works, but no other hotkeys.

With xev in the terminal window, my left alt key gives the following output:


FocusOut event, serial 31, synthetic NO, window 0x2600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x2600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  4294967243 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0


or sometimes


FocusOut event, serial 31, synthetic NO, window 0x2600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x2600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

and the right alt key gives the following output:

FocusOut event, serial 31, synthetic NO, window 0x2600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x2600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

or sometimes

FocusOut event, serial 31, synthetic NO, window 0x2600001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x2600001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  1   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0


As you can see, when I press the alt keys, the window looses its focus. How can I restore the keys to their normal behaviour?

Shouldn't it be something similar to what Ctrl results in?

KeyPress event, serial 31, synthetic NO, window 0x2600001,
    root 0x59, subw 0x0, time 2357674, (-187,-229), root:(908,359),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x2600001,
    root 0x59, subw 0x0, time 2357769, (-187,-229), root:(908,359),
    state 0x14, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

---

### Post by olejorgen on 2008-10-02
I'd guess some app is stealing alt presses. Have you changed hotkeys in some application lately?

Post the output from:```
xmodmap
```

---

### Post by sebiolo on 2008-10-02
I got the right alt key to work with the program xkeycaps. But this did not work on the left key.

So I created a new user, and there the left alt key worked (but for some reason the tab key didn't!). When I logged back to my old account, the left alt key worked there as well, and both keys now produces a normal output with xev.

However, for some reason, the super key doesn't work anymore. I used to be able to use super + tab, but now the super is completely dead. Can't get it to work with xkeycaps either. The xev output is normal, however. :-k

---

