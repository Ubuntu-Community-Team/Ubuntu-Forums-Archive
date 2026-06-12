---
title: "Volume Controls not working in 11.04"
date: 2011-06-21
forum: Hardware
---

### Post by emmiesix on 2011-06-21
I have a Dell Inspiron 1750.  Pressing the Fn+F7, F8 or F9 keys (mute, volume down, volume up) does not work or bring up the notification window like it did up to last week.

Key bindings, however, still seem to be correct... can anyone help me figure out where to look next?  Right now I have to open up the sound manager to change volume or mute.


results of hitting each of these in xev:
```

KeyRelease event, serial 32, synthetic NO, window 0x5000001,
    root 0xaf, subw 0x0, time 126672779, (180,216), root:(184,330),
    state 0x10, keycode 122 (keysym 0x1008ff11, XF86AudioLowerVolume), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 32, synthetic NO, window 0x5000001,
    root 0xaf, subw 0x0, time 126673673, (180,216), root:(184,330),
    state 0x10, keycode 121 (keysym 0x1008ff12, XF86AudioMute), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 32, synthetic NO, window 0x5000001,
    root 0xaf, subw 0x0, time 126673683, (180,216), root:(184,330),
    state 0x10, keycode 121 (keysym 0x1008ff12, XF86AudioMute), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

---

### Post by emmiesix on 2011-06-21
Well, I just realized I was logged into the "no effects" ubuntu classic mode somehow, so that fixes it.  Sorry.

---

