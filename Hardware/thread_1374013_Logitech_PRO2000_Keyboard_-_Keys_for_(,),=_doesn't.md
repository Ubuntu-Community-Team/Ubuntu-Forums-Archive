---
title: "Logitech PRO2000 Keyboard - Keys for (,),= doesn't work"
date: 2010-01-06
forum: Hardware
---

### Post by mickoz84 on 2010-01-06
Hello, 

I have a problem with my Logitech PRO2000 wireless keyboard. The Keyboard works fine under Ubuntu 9.10, also most of the special keys for calculator or loudness etc. works.

The Problem are the keys above the Numpad. There are special keys for '=', '(', ')' placed. But they doesn't work under Ubuntu.

Here is the relevant output from xev:
```

KeyPress event, serial 36, synthetic NO, window 0x4c00001,
    root 0x13c, subw 0x0, time 9261583, (85,-7), root:(1397,866),
    state 0x10, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4c00001,
    root 0x13c, subw 0x0, time 9261583, (85,-7), root:(1397,866),
    state 0x18, keycode 83 (keysym 0xffb4, KP_4), same_screen YES,
    XLookupString gives 1 bytes: (34) "4"
    XmbLookupString gives 1 bytes: (34) "4"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
    root 0x13c, subw 0x0, time 9261599, (85,-7), root:(1397,866),
    state 0x18, keycode 83 (keysym 0xffb4, KP_4), same_screen YES,
    XLookupString gives 1 bytes: (34) "4"
    XFilterEvent returns: False

KeyPress event, serial 36, synthetic NO, window 0x4c00001,
    root 0x13c, subw 0x0, time 9261599, (85,-7), root:(1397,866),
    state 0x18, keycode 90 (keysym 0xffb0, KP_0), same_screen YES,
    XLookupString gives 1 bytes: (30) "0"
    XmbLookupString gives 1 bytes: (30) "0"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
    root 0x13c, subw 0x0, time 9261623, (85,-7), root:(1397,866),
    state 0x18, keycode 90 (keysym 0xffb0, KP_0), same_screen YES,
    XLookupString gives 1 bytes: (30) "0"
    XFilterEvent returns: False

KeyRelease event, serial 36, synthetic NO, window 0x4c00001,
    root 0x13c, subw 0x0, time 9261639, (85,-7), root:(1397,866),
    state 0x18, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

It seems that the keyboard emulates the keys with the keycombination ALT_L + (4, 0).

Is there a possibility to use that keys in Ubuntu?

Sorry for my bad english ;-)

---

### Post by mickoz84 on 2010-01-06
No idea or is it not possible?

---

