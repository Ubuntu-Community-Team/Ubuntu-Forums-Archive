---
title: "One key does not work on laptop"
date: 2007-09-21
forum: Hardware &amp; Laptops
---

### Post by 315234 on 2007-09-21
I have an acer 5600 series laptop, and the '4' key does not work. I suspect it has something to do with the Euro sign on that key.

Some xev outputs for stated keys:

'3' key:
```
KeyPress event, serial 27, synthetic NO, window 0xc00001,
    root 0x5c, subw 0x0, time 667431086, (-98,80), root:(453,399),
    state 0x0, keycode 12 (keysym 0x33, 3), same_screen YES,
    XLookupString gives 1 bytes: (33) "3"
    XmbLookupString gives 1 bytes: (33) "3"
    XFilterEvent returns: False

KeyRelease event, serial 27, synthetic NO, window 0xc00001,
    root 0x5c, subw 0x0, time 667431167, (-98,80), root:(453,399),
    state 0x0, keycode 12 (keysym 0x33, 3), same_screen YES,
    XLookupString gives 1 bytes: (33) "3"
```

'4' key:
```
FocusOut event, serial 27, synthetic NO, window 0xc00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 27, synthetic NO, window 0xc00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 27, synthetic NO, window 0x0,
    keys:  2   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
```

'$' key (shift-4):
```
KeyPress event, serial 24, synthetic NO, window 0xc00001,
    root 0x5c, subw 0x0, time 667541220, (-228,168), root:(323,487),
    state 0x0, keycode 62 (keysym 0xffe2, Shift_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 27, synthetic NO, window 0xc00001,
    root 0x5c, subw 0x0, time 667542667, (-228,168), root:(323,487),
    state 0x1, keycode 13 (keysym 0x24, dollar), same_screen YES,
    XLookupString gives 1 bytes: (24) "$"
    XmbLookupString gives 1 bytes: (24) "$"
    XFilterEvent returns: False

KeyRelease event, serial 27, synthetic NO, window 0xc00001,
    root 0x5c, subw 0x0, time 667542748, (-228,168), root:(323,487),
    state 0x1, keycode 13 (keysym 0x24, dollar), same_screen YES,
    XLookupString gives 1 bytes: (24) "$"

KeyRelease event, serial 27, synthetic NO, window 0xc00001,
    root 0x5c, subw 0x0, time 667543158, (-228,168), root:(323,487),
    state 0x1, keycode 62 (keysym 0xffe2, Shift_R), same_screen YES,
    XLookupString gives 0 bytes: 
```

'€' key (AltGr-4):
```
KeyPress event, serial 24, synthetic NO, window 0xc00001,
    root 0x5c, subw 0x0, time 667620328, (-67,122), root:(484,441),
    state 0x0, keycode 113 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 27, synthetic NO, window 0xc00001,
    root 0x5c, subw 0x0, time 667621423, (-67,122), root:(484,441),
    state 0x80, keycode 13 (keysym 0x20ac, EuroSign), same_screen YES,
    XLookupString gives 3 bytes: (e2 82 ac) "€"
    XmbLookupString gives 3 bytes: (e2 82 ac) "€"
    XFilterEvent returns: False

KeyRelease event, serial 27, synthetic NO, window 0xc00001,
    root 0x5c, subw 0x0, time 667621509, (-67,122), root:(484,441),
    state 0x80, keycode 13 (keysym 0x20ac, EuroSign), same_screen YES,
    XLookupString gives 3 bytes: (e2 82 ac) "€"

KeyRelease event, serial 27, synthetic NO, window 0xc00001,
    root 0x5c, subw 0x0, time 667621755, (-67,122), root:(484,441),
    state 0x80, keycode 113 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XLookupString gives 0 bytes: 
```

'¼' key (shift-AltGr-4):
```
KeyPress event, serial 24, synthetic NO, window 0xc00001,
    root 0x5c, subw 0x0, time 667642627, (-119,152), root:(432,471),
    state 0x0, keycode 113 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 27, synthetic NO, window 0xc00001,
    root 0x5c, subw 0x0, time 667642956, (-119,152), root:(432,471),
    state 0x80, keycode 62 (keysym 0xffe2, Shift_R), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 27, synthetic NO, window 0xc00001,
    root 0x5c, subw 0x0, time 667643565, (-119,152), root:(432,471),
    state 0x81, keycode 13 (keysym 0xbc, onequarter), same_screen YES,
    XLookupString gives 2 bytes: (c2 bc) "¼"
    XmbLookupString gives 2 bytes: (c2 bc) "¼"
    XFilterEvent returns: False

KeyRelease event, serial 27, synthetic NO, window 0xc00001,
    root 0x5c, subw 0x0, time 667643673, (-119,152), root:(432,471),
    state 0x81, keycode 13 (keysym 0xbc, onequarter), same_screen YES,
    XLookupString gives 2 bytes: (c2 bc) "¼"

KeyRelease event, serial 27, synthetic NO, window 0xc00001,
    root 0x5c, subw 0x0, time 667644863, (-119,152), root:(432,471),
    state 0x81, keycode 62 (keysym 0xffe2, Shift_R), same_screen YES,
    XLookupString gives 0 bytes: 

KeyRelease event, serial 27, synthetic NO, window 0xc00001,
    root 0x5c, subw 0x0, time 667644866, (-119,152), root:(432,471),
    state 0x80, keycode 113 (keysym 0xfe03, ISO_Level3_Shift), same_screen YES,
    XLookupString gives 0 bytes: 
```

'4' key (on the Fn-Keypad keys) (requires numlock to be on):
```
KeyPress event, serial 27, synthetic NO, window 0xc00001,
    root 0x5c, subw 0x0, time 667715195, (-106,153), root:(445,472),
    state 0x10, keycode 83 (keysym 0xffb4, KP_4), same_screen YES,
    XLookupString gives 1 bytes: (34) "4"
    XmbLookupString gives 1 bytes: (34) "4"
    XFilterEvent returns: False

KeyRelease event, serial 27, synthetic NO, window 0xc00001,
    root 0x5c, subw 0x0, time 667715258, (-106,153), root:(445,472),
    state 0x10, keycode 83 (keysym 0xffb4, KP_4), same_screen YES,
    XLookupString gives 1 bytes: (34) "4"

```

I see the problem but do not know what to do about it. Can anyone out there help?

---

### Post by wjp.reg on 2007-09-21
Have you tried going into System | Preferences | Keyboard and seeing if your keyboard model is available or can be added?

I used this successfully with my Lenovo.

---

### Post by 315234 on 2007-09-27
I am using Debian. The Xkbmodel is set to pc104.

I notice that the keyboard works fine on tty, so this must be a problem with X.

setxkbmap -print:
```
xkb_keymap {
        xkb_keycodes  { include "xfree86+aliases(qwerty)"       };
        xkb_types     { include "complete"      };
        xkb_compat    { include "complete"      };
        xkb_symbols   { include "pc(pc105)+gb"  };
        xkb_geometry  { include "pc(pc104)"     };
};
```

---

