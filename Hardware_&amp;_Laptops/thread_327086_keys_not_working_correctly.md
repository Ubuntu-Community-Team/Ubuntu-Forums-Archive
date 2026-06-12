---
title: "keys not working correctly"
date: 2006-12-28
forum: Hardware &amp; Laptops
---

### Post by Reb on 2006-12-28
Hey-
My F(1-12) keys don't seem to be working very well - at least, some of them. Alt-F2 doesn't work for launch dialog - in fact, nothing seems to work.  The F3-F5 keys worked for Mute, Vol Up and Vol Down until I deleted those settings from the gnome keyboard shortcuts, but that's another story.  F11, mapped in beryl to show desktop is the only one that does work, and it doesn't look like the others in xev when pressed, instead is somethin like this:
FocusOut event, serial 32, synthetic NO, window 0x3e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusOut event, serial 32, synthetic NO, window 0x3e00001,
    mode NotifyWhileGrabbed, detail NotifyNonlinear

PropertyNotify event, serial 32, synthetic NO, window 0x3e00001,
    atom 0x1b8 (_NET_WINDOW_DECOR), time 3405202408, state PropertyNewValue

ConfigureNotify event, serial 32, synthetic NO, window 0x3e00001,
    event 0x3e00001, window 0x3e00001, (3,47), width 178, height 178,
    border_width 2, above 0x340058c, override NO
F9 and F10 are similarly mapped in beryl, but do not work at all. Any ideas?

---

### Post by Reb on 2006-12-31
anything, anyone?

---

### Post by Reb on 2007-01-08
This is really, kind of, a big deal.

---

### Post by Reb on 2007-01-09
Any answers?

---

### Post by golem3 on 2007-01-11
Yeah, no one seems to know. I am having a similar issue.

---

