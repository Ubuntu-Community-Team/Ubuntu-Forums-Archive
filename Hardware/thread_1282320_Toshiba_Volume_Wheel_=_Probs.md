---
title: "Toshiba Volume Wheel = Probs"
date: 2009-10-04
forum: Hardware
---

### Post by SpinBoldak on 2009-10-04
I've done a search and I can't find a problem quite like mine, so apologies from the Noob if this has been covered ad nauseum.

I've installed 9.04 on my Toshiba U305-S5107.

Problem - the volume wheel causes the volume indicator (top-right pop-up one, not on the toolbar) to flash and run up and down. A simple bump of the wheel causes this for a minute or so. The volume ends up muted and the keyboard no longer works after this.

I've remapped the volume controls to another key combination and it no longer causes the keyboard to crash or the volume icon to flash, but I'd like to use my volume wheel.

xev returns a _stream_ of these messages when I move the wheel just once:

KeyPress event, serial 35, synthetic NO, window 0x4800001,
    root 0xaa, subw 0x0, time 5806918, (-58,345), root:(616,396),
    state 0x0, keycode 123 (keysym 0x1008ff13, XF86AudioRaiseVolume), same_screen YES,
    XLookupString gives 0 bytes:
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False



Any suggestions?

---

### Post by TheSumo on 2010-05-06
Bump, I guess.

I recently installed Ubuntu 10.04 on my friend's Toshiba laptop and he is having the exact same problem.  Anyone have a fix for this?

Or, at least, how do you remap volume controls, like Spinboldak did?

Thanks

Sumo

---

