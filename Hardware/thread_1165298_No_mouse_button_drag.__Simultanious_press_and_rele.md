---
title: "No mouse button drag.  Simultanious press and release error."
date: 2009-05-20
forum: Hardware
---

### Post by spoonerism on 2009-05-20
On Ubuntu 9.04 - I have a macbook pro and a targus usb optical mouse.

I can't click and drag with my middle mouse button.  The problem, as far as I can tell, with `xev` - is the press is not detected till I release the mouse.

So instead of say, clicking and then getting a mouse press event, and then holding for a while and release and then getting a mouse release event ( expected behaviour )-

I have

I click, get no event, hold, and when I release the mouse I get a press event then a release event.

xev output:

ButtonPress event, serial 35, synthetic NO, window 0x3e00001,
    root 0x13c, subw 0x0, time 1616950, (174,103), root:(181,794),
    state 0x0, button 2, same_screen YES

ButtonRelease event, serial 35, synthetic NO, window 0x3e00001,
    root 0x13c, subw 0x0, time 1616958, (174,103), root:(181,794),
    state 0x200, button 2, same_screen YES

---

