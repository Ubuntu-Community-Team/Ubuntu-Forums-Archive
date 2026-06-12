---
title: "USB Keyboard -- not all keys available"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by ChrisMP1 on 2007-12-14
I used to use an Apple computer, so I have an Apple USB keyboard that I use with Ubuntu. Sometime between Mac OS X and Ubuntu, I tried Debian. In Debian (and obviously on the Mac), all of the top row keys (Esc, F1-F16, Volume, Eject) were usable (I configured them through xbindkeys). I had a certain setup mapped out that I was adjusted to, and I want to still use it. However, it needed the F16 key, and in Ubuntu, neither the Keyboard Shortcuts configuration panel nor xbindkeys recognize F16 (only key not working). How do I make F16 available?

---

### Post by diatribe on 2007-12-14
use xev to see if it is recognised at all

---

### Post by ChrisMP1 on 2007-12-14
It shows up. However, the other keys show up like this example (F15):

```
KeyPress event, serial 28, synthetic NO, window 0x4200001,
    root 0x5e, subw 0x0, time 3688053456, (3,-119), root:(1390,396),
    state 0x10, keycode 184 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x4200001,
    root 0x5e, subw 0x0, time 3687711953, (-49,-120), root:(1338,395),
    state 0x10, keycode 184 (keysym 0x0, NoSymbol), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

While F16 shows up with other events, as:

```
KeyPress event, serial 28, synthetic NO, window 0x4200001,
    root 0x5e, subw 0x0, time 3688097065, (10,-84), root:(1397,431),
    state 0x10, keycode 93 (keysym 0xff7e, Mode_switch), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

PropertyNotify event, serial 31, synthetic NO, window 0x4200001,
    atom 0x110 (XKLAVIER_STATE), time 3688097068, state PropertyNewValue

KeyRelease event, serial 31, synthetic NO, window 0x4200001,
    root 0x5e, subw 0x0, time 3688097152, (10,-84), root:(1397,431),
    state 0x10, keycode 93 (keysym 0xff7e, Mode_switch), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

PropertyNotify event, serial 31, synthetic NO, window 0x4200001,
    atom 0x110 (XKLAVIER_STATE), time 3688097154, state PropertyNewValue


```

---

