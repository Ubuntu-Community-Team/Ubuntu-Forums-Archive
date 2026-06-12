---
title: "Keyboard problem after upgrade"
date: 2009-11-03
forum: Installation &amp; Upgrades
---

### Post by janerikdahlin on 2009-11-03
The arrow keys + insert, delete, home, end, PgUp, and PgDown keys stopped working after upgrading. However Shift + the same key works fine.

According to xev the keys produces strange events. A tap on the Up arrow gives the following events:

```

FocusOut event, serial 33, synthetic NO, window 0x4200001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 33, synthetic NO, window 0x4200001,
    mode NotifyUngrab, detail NotifyPointer

FocusIn event, serial 33, synthetic NO, window 0x4200001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  55  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

```

Shift-Up gives the expected events:

```

KeyPress event, serial 33, synthetic NO, window 0x4200001,
    root 0x237, subw 0x0, time 2104309, (111,63), root:(1317,109),
    state 0x11, keycode 111 (keysym 0xff52, Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic NO, window 0x4200001,
    root 0x237, subw 0x0, time 2104365, (111,63), root:(1317,109),
    state 0x11, keycode 111 (keysym 0xff52, Up), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

```

The keyboard is an old PC104 with a PS2(?) connector. 
The update manager commented out the InputDevice parts in xorg.conf.

Any help would be appreciated.

---

### Post by janerikdahlin on 2009-11-04
This problem seems to be gnome related. The keys work fine in kde.

---

