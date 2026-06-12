---
title: "Recursive digit appears"
date: 2014-07-28
forum: Hardware
---

### Post by Mr.Kappa on 2014-07-28
Maybe it's the wrong place to ask but... I have PC that's always been running ubuntu, it's been a while now that randomly zero digits appear on every application I use like the zero button on my keyboard is pressed. I've tried changing keyboards, cleaning the port and disconetting the keyboard from the pc but the zero digits still appear.
Can someone tell me how can I solve this issue?

---

### Post by tgalati4 on 2014-07-28
Open a terminal and run *xev*.  Put the mouse in the *xev* box and observe the output.  A normal zero press and release would look like:

> KeyPress event, serial 35, synthetic NO, window 0x4200001,
    root 0xad, subw 0x0, time 45139215, (165,3), root:(171,51),
    state 0x0, keycode 19 (keysym 0x30, 0), same_screen YES,
    XLookupString gives 1 bytes: (30) "0"
    XmbLookupString gives 1 bytes: (30) "0"
    XFilterEvent returns: False

KeyRelease event, serial 38, synthetic NO, window 0x4200001,
    root 0xad, subw 0x0, time 45139354, (165,3), root:(171,51),
    state 0x0, keycode 19 (keysym 0x30, 0), same_screen YES,
    XLookupString gives 1 bytes: (30) "0"
    XFilterEvent returns: False


We need to isolate if it is a kernel problem, and xserver/xinput problem, or a keyboard/hardware problem.  Check /var/log/Xorg.log.0 for input errors.

---

