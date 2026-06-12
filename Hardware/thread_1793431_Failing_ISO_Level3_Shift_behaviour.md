---
title: "Failing ISO_Level3_Shift behaviour"
date: 2011-06-29
forum: Hardware
---

### Post by msmarino on 2011-06-29
Hi all!

Apologies if this is not the correct forum for this problem.

I am having an unusual problem with my keyboard.  I use Spanish layout with common symbols available via Alt-Gr (ISO_Level3_Shift) which works intermittently.

I am using a Microsoft Wireless Multimedia Keyboard 1.1 with Ubuntu 10.04.2 (fully updated) under VirtualBox 4.0.10 on a Windows 7 host (which does NOT present ANY problems or unusual behaviours).


xev gives me
```
KeyPress event, serial 33, synthetic NO, window 0x5200001,
    root 0x107, subw 0x0, time 481221, (151,-17), root:(1087,94),
    state 0x10, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

[B][INDENT]KeyPress event, serial 33, synthetic NO, window 0x5200001,
    root 0x107, subw 0x0, time 481465, (151,-17), root:(1087,94),
    state 0x90, keycode 11 (keysym 0x40, at), same_screen YES,
    XLookupString gives 1 bytes: (40) "@"
    XmbLookupString gives 1 bytes: (40) "@"
    XFilterEvent returns: False[/INDENT][/B]

KeyRelease event, serial 33, synthetic NO, window 0x5200001,
    root 0x107, subw 0x0, time 481504, (151,-17), root:(1087,94),
    state 0x90, keycode 11 (keysym 0x40, at), same_screen YES,
    XLookupString gives 1 bytes: (40) "@"
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x5200001,
    root 0x107, subw 0x0, time 483209, (151,-17), root:(1087,94),
    state 0x90, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic NO, window 0x5200001,
    root 0x107, subw 0x0, time 483774, (151,-17), root:(1087,94),
    state 0x10, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x5200001,
    root 0x107, subw 0x0, time 483858, (151,-17), root:(1087,94),
    state 0x11, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic NO, window 0x5200001,
    root 0x107, subw 0x0, time 484430, (151,-17), root:(1087,94),
    state 0x10, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic NO, window 0x5200001,
    root 0x107, subw 0x0, time 484431, (151,-17), root:(1087,94),
    state 0x14, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

[B][INDENT]KeyPress event, serial 33, synthetic NO, window 0x5200001,
    root 0x107, subw 0x0, time 484736, (151,-17), root:(1087,94),
    state 0x94, keycode 11 (keysym 0x40, at), same_screen YES,
    XLookupString gives 1 bytes: (00) ""
    XmbLookupString gives 1 bytes: (00) ""
    XFilterEvent returns: False[/INDENT][/B]

KeyRelease event, serial 33, synthetic NO, window 0x5200001,
    root 0x107, subw 0x0, time 484813, (151,-17), root:(1087,94),
    state 0x94, keycode 11 (keysym 0x40, at), same_screen YES,
    XLookupString gives 1 bytes: (00) ""
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x5200001,
    root 0x107, subw 0x0, time 485717, (151,-17), root:(1087,94),
    state 0x94, keycode 37 (keysym 0xffe3, Control_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x5200001,
    root 0x107, subw 0x0, time 485717, (151,-17), root:(1087,94),
    state 0x90, keycode 108 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XKeysymToKeycode returns keycode: 92
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False
```

***_Explanation:_***
First 2 keypress/release show correct functioning of Alt-Gr. See first bold & indented keypress.
Then I press Left-Shift
Now Alt-Gr+2 correctly indicates that I have pressed 'at' but I get no char.  Please observe the 2nd bold & indented key press.

Also of note is that initially Alt-Gr raises only Level3 events, but after Shift_L keypress it raises both Control_L & Level3 events.

Any assistance would be appreciated.

---

### Post by msmarino on 2011-06-29
I have now found that if I press Control_L + Level3 (Alt_R) I can get back to normal working state and access to Level3 chars.

A workaround but certainly no solution.

Hope someone can shed some light!

---

