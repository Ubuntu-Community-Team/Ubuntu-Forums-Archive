---
title: "dv8230us Media Key Issues"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by armware on 2008-02-15
Running Kubuntu Gusty, KDE 3.5.8

I'm really only worried about the volume controls (up/down/mute).
Pressing up or down will display the volume thing on the screen, and it moves up and down accordingly, but the actual volume doesn't change at all. The mute button does, however, mute the sound.

I fired up xev and pressed the keys (in order: volume down, mute, volume up), and this is what I get:
```
KeyRelease event, serial 28, synthetic NO, window 0x4400001,
    root 0x52, subw 0x0, time 498778747, (1070,599), root:(1079,629),
    state 0x10, keycode 174 (keysym 0x1008ff11, XF86AudioLowerVolume), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x4400001,
    root 0x52, subw 0x0, time 498780468, (1070,599), root:(1079,629),
    state 0x10, keycode 160 (keysym 0x1008ff12, XF86AudioMute), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False

KeyRelease event, serial 31, synthetic NO, window 0x4400001,
    root 0x52, subw 0x0, time 498782120, (1070,599), root:(1079,629),
    state 0x10, keycode 176 (keysym 0x1008ff13, XF86AudioRaiseVolume), same_screen YES,
    XLookupString gives 0 bytes:
    XFilterEvent returns: False
```

I don't know where to go from here.

Other things I've tried that had no affect are changing the kmix master channel, and re-applying the global keys for the volume controls both in kmix and kcontrol. None of this changed anything.

---

