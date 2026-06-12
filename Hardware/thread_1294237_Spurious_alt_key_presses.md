---
title: "Spurious alt key presses"
date: 2009-10-18
forum: Hardware
---

### Post by Uffish on 2009-10-18
Hi gurus,

I have a most annoying problem of spurious alt key presses. I fired up xev and indeed, when I don't do nothing I occasionally get a couple of events like this:

KeyPress event, serial 35, synthetic NO, window 0x4000001,
    root 0xac, subw 0x0, time 3397837, (109,107), root:(116,158),
    state 0x0, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyRelease event, serial 35, synthetic NO, window 0x4000001,
    root 0xac, subw 0x0, time 3397837, (109,107), root:(116,158),
    state 0x8, keycode 64 (keysym 0xffe9, Alt_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

Notice the times! In a normal keypress you would never have the exact same time for both the press and the release. I don't believe it's a hardware problem per-se because I don't see this on windowz. Any solution or workaround? This is really annoying...

I'm using ubuntu 9.04 fully updated, and the computer is a compaq presario laptop.

Thx,

---

### Post by Edemoe on 2012-02-17
The same problem here on 11.10. Have you found any solution?

---

### Post by Edemoe on 2012-02-17
Replying to myself: Never run Totem - it's pressing your Alt. (It's not a problem in Unity itself but Openoffice and Windows in VirtualBox are quite annoying.

---

