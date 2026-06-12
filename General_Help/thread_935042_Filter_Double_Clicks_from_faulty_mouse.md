---
title: "Filter Double Clicks from faulty mouse"
date: 2008-10-01
forum: General Help
---

### Post by Eoghan Murray on 2008-10-01
Hi,

The mouse I'm using has recently sporadically started sending two click events for a single click.  This is quite annoying!

When I run ```
xev
``` the relevant output is:

```
ButtonPress event, serial 30, synthetic NO, window 0x3c00001,
    root 0x329, subw 0x0, time 14559276, (73,137), root:(1358,161),
    state 0x10, button 1, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x3c00001,
    root 0x329, subw 0x0, time 14559276, (73,137), root:(1358,161),
    state 0x110, button 1, same_screen YES

ButtonPress event, serial 30, synthetic NO, window 0x3c00001,
    root 0x329, subw 0x0, time 14559347, (73,137), root:(1358,161),
    state 0x10, button 1, same_screen YES

ButtonRelease event, serial 30, synthetic NO, window 0x3c00001,
    root 0x329, subw 0x0, time 14559372, (73,137), root:(1358,161),
    state 0x110, button 1, same_screen YES

```


I understand that this is quite a common problem as mice age — what I would like is a software solution to this hardware problem, rather than throwing away an otherwise perfectly operational mouse.

Does anyone have any idea how I could begin to hack ?xorg? in order to filter such events (I'm assuming it's physically impossible to actually press the mouse key twice in such a short space of time).  Or is there an existing solution out there?

Thanks!

---

