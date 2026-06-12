---
title: "Remapping a key to a mouse button / Forcing a mouse button act as a mouse button"
date: 2008-11-07
forum: Hardware
---

### Post by kub-fu on 2008-11-07
Hi,

I have a Logitech Revolution MX, and I want the button that's below the scroll wheel to act as a middle mouse button. Currently, that button is mapped to XF86Search.

I've read about xinit, xmodmap, and xbindkeys, but so far I haven't found how to accomplish this.

This seems complicated because on xev, that button doesn't seem to fire a mouse button event at all:

```
MappingNotify event, serial 30, synthetic NO, window 0x0,
    request MappingKeyboard, first_keycode 8, count 247

FocusIn event, serial 30, synthetic NO, window 0x4a00001,
    mode NotifyGrab, detail NotifyPointer

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  4294967289 0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   2   0   0   0   

FocusOut event, serial 34, synthetic NO, window 0x4a00001,
    mode NotifyUngrab, detail NotifyPointer

PropertyNotify event, serial 34, synthetic NO, window 0x4a00001,
    atom 0x13e (_NET_WM_ICON_GEOMETRY), time 78727426, state PropertyNewValue

```

If I disable that shortcut (System>Preferences>Keyboard Shortcuts), xev now shows a KeyPress and a KeyRelease for keycode 225 (XF86Search) when I press the button.

My current workaround is to use xmodmap to remap the thumb button as the middle button.

I'm on Ubuntu 8.10 (on previous versions I used btnx to accomplish this).

Thanks!

---

