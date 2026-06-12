---
title: "Write script for special key (on keyboard)"
date: 2008-11-07
forum: Hardware
---

### Post by garmada on 2008-11-07
I have special key on keyboard and i have belkin n52te and i need configure special key for system, for example when i hit button 15 on belkin run terminal. Thanks for help.

---

### Post by cdtech on 2008-11-07
Some keys just work because they are hardwired to do so. I have FN key's and all of mine do what their labeled to do.

Using the command line "xev" will let you see the keycodes that are associated with the key combinations that you wish to use.

If you use "xev" and see nothing from the combination that could mean that there are no keycodes associated with that combination.

These are the keycodes for the "p" key I pressed on my keyboard:
```
KeyPress event, serial 34, synthetic NO, window 0x6400001,
    root 0x52, subw 0x0, time 2010007620, (523,557), root:(526,613),
    state 0x10, **keycode** 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (70) "p"
    XmbLookupString gives 1 bytes: (70) "p"
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x6400001,
    root 0x52, subw 0x0, time 2010007725, (523,557), root:(526,613),
    state 0x10, **keycode** 33 (keysym 0x70, p), same_screen YES,
    XLookupString gives 1 bytes: (70) "p"
    XFilterEvent returns: False
```

The keycodes that can be attached to a scancode can be found in "/usr/include/linux/input.h"

The command to set: `setkeycodes <scancode> <keycode>`

I hope this gives you a direction to your solution. Just search the net for scancodes and keycodes for more information.

---

