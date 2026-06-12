---
title: "Delete key returns 1 in bash"
date: 2010-05-11
forum: Hardware
---

### Post by hedge.hog on 2010-05-11
Hi,
On my logitch LX700 keyboard the 'Delete' key returns 1 in bash.
In some apps like firefox it does not do anything.

Looking around I've only seen a suggestion to get data from xev, but no suggestion about what do with that data.

When I press 'Delete' the key press data is below.  A noticable difference to a functioning key is that for a working key I see ```
same_screen YES
```:

```

KeyPress event, serial 33, synthetic YES, window 0x9a00001,
    root 0x27d, subw 0x2298490, time 3176696084, (257,0), root:(1,0),
    state 0x0, keycode 10 (keysym 0x31, 1), same_screen NO,
    XLookupString gives 1 bytes: (31) "1"
    XmbLookupString gives 1 bytes: (31) "1"
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic YES, window 0x9a00001,
    root 0x27d, subw 0x2298490, time 3176696084, (257,0), root:(1,0),
    state 0x0, keycode 10 (keysym 0x31, 1), same_screen NO,
    XLookupString gives 1 bytes: (31) "1"
    XFilterEvent returns: False
```The full xev output is:
```

$ xev
Outer window is 0x9a00001, inner window is 0x9a00002

PropertyNotify event, serial 8, synthetic NO, window 0x9a00001,
    atom 0x27 (WM_NAME), time 320082309, state PropertyNewValue

PropertyNotify event, serial 9, synthetic NO, window 0x9a00001,
    atom 0x22 (WM_COMMAND), time 320082309, state PropertyNewValue

PropertyNotify event, serial 10, synthetic NO, window 0x9a00001,
    atom 0x28 (WM_NORMAL_HINTS), time 320082309, state PropertyNewValue

CreateNotify event, serial 11, synthetic NO, window 0x9a00001,
    parent 0x9a00001, window 0x9a00002, (10,10), width 50, height 50
border_width 4, override NO

PropertyNotify event, serial 14, synthetic NO, window 0x9a00001,
    atom 0x114 (WM_PROTOCOLS), time 320082310, state PropertyNewValue

MapNotify event, serial 15, synthetic NO, window 0x9a00001,
    event 0x9a00001, window 0x9a00002, override NO

ConfigureNotify event, serial 20, synthetic NO, window 0x9a00001,
    event 0x9a00001, window 0x9a00001, (0,0), width 178, height 178,
    border_width 0, above 0x7a1e6b3, override NO

PropertyNotify event, serial 20, synthetic NO, window 0x9a00001,
    atom 0x165 (_NET_WM_ALLOWED_ACTIONS), time 320082310, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x9a00001,
    atom 0x165 (_NET_WM_ALLOWED_ACTIONS), time 320082310, state PropertyNewValue

ReparentNotify event, serial 20, synthetic NO, window 0x9a00001,
    event 0x9a00001, window 0x9a00001, parent 0x26df88a,
    (0,0), override NO

PropertyNotify event, serial 20, synthetic NO, window 0x9a00001,
    atom 0x11c (_NET_WM_DESKTOP), time 320082311, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x9a00001,
    atom 0x11c (_NET_WM_DESKTOP), time 320082311, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x9a00001,
    atom 0x119 (_NET_FRAME_EXTENTS), time 320082311, state PropertyNewValue

ConfigureNotify event, serial 20, synthetic NO, window 0x9a00001,
    event 0x9a00001, window 0x9a00001, (1,29), width 178, height 178,
    border_width 0, above 0x0, override NO

PropertyNotify event, serial 20, synthetic NO, window 0x9a00001,
    atom 0x13a (WM_STATE), time 320082311, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x9a00001,
    atom 0x122 (_NET_WM_STATE), time 320082311, state PropertyNewValue

PropertyNotify event, serial 20, synthetic NO, window 0x9a00001,
    atom 0x182 (XKLAVIER_STATE), time 320082314, state PropertyNewValue

ConfigureNotify event, serial 20, synthetic YES, window 0x9a00001,
    event 0x9a00001, window 0x9a00001, (12,71), width 178, height 178,
    border_width 2, above 0x0, override NO

MapNotify event, serial 20, synthetic NO, window 0x9a00001,
    event 0x9a00001, window 0x9a00001, override NO

VisibilityNotify event, serial 20, synthetic NO, window 0x9a00001,
    state VisibilityUnobscured

Expose event, serial 20, synthetic NO, window 0x9a00001,
    (0,0), width 178, height 10, count 3

Expose event, serial 20, synthetic NO, window 0x9a00001,
    (0,10), width 10, height 58, count 2

Expose event, serial 20, synthetic NO, window 0x9a00001,
    (68,10), width 110, height 58, count 1

Expose event, serial 20, synthetic NO, window 0x9a00001,
    (0,68), width 178, height 110, count 0

PropertyNotify event, serial 20, synthetic NO, window 0x9a00001,
    atom 0x122 (_NET_WM_STATE), time 320082316, state PropertyNewValue

FocusIn event, serial 20, synthetic NO, window 0x9a00001,
    mode NotifyNormal, detail NotifyNonlinear

KeymapNotify event, serial 20, synthetic NO, window 0x0,
    keys:  4294967230 0   0   0   16  0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

PropertyNotify event, serial 20, synthetic NO, window 0x9a00001,
    atom 0x122 (_NET_WM_STATE), time 320082316, state PropertyNewValue

KeyRelease event, serial 29, synthetic NO, window 0x9a00001,
    root 0x27d, subw 0x0, time 320082341, (16,-11), root:(30,62),
    state 0x0, keycode 36 (keysym 0xff0d, Return), same_screen YES,
"   XLookupString gives 1 bytes: (0d) "
    XFilterEvent returns: False

PropertyNotify event, serial 32, synthetic NO, window 0x9a00001,
    atom 0x15b (_NET_WM_ICON_GEOMETRY), time 320082388, state PropertyNewValue

FocusOut event, serial 33, synthetic NO, window 0x9a00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 33, synthetic NO, window 0x9a00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 33, synthetic NO, window 0x0,
    keys:  4294967230 0   0   0   0   0   0   0   0   0   0   0   0   0   4294967168 0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   

KeyRelease event, serial 33, synthetic NO, window 0x9a00001,
    root 0x27d, subw 0x0, time 320083981, (16,-11), root:(30,62),
    state 0x0, keycode 119 (keysym 0xffff, Delete), same_screen YES,
    XLookupString gives 1 bytes: (7f) ""
    XFilterEvent returns: False

KeyPress event, serial 33, synthetic YES, window 0x9a00001,
    root 0x27d, subw 0x2298490, time 3176696084, (257,0), root:(1,0),
    state 0x0, keycode 10 (keysym 0x31, 1), same_screen NO,
    XLookupString gives 1 bytes: (31) "1"
    XmbLookupString gives 1 bytes: (31) "1"
    XFilterEvent returns: False

KeyRelease event, serial 33, synthetic YES, window 0x9a00001,
    root 0x27d, subw 0x2298490, time 3176696084, (257,0), root:(1,0),
    state 0x0, keycode 10 (keysym 0x31, 1), same_screen NO,
    XLookupString gives 1 bytes: (31) "1"
    XFilterEvent returns: False

ClientMessage event, serial 33, synthetic YES, window 0x9a00001,
    message_type 0x114 (WM_PROTOCOLS), format 32, message 0x112 (WM_DELETE_WINDOW)

```Appreciate any hints or tips.

---

