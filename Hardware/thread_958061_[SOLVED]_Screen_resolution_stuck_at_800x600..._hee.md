---
title: "[SOLVED] Screen resolution stuck at 800x600... heeelllp. lol"
date: 2008-10-25
forum: Hardware
---

### Post by wardrich on 2008-10-25
So I recently updated from gutsy to hardy, and all has been fairly well, but I have no idea what's happening.  The only thing I recall installing yesterday was kdm and dosbox.  gdm was acting up, so I figured if I threw on kdm it would make things better... I think I was wrong.  lol.  If I try to change the screen resolution from the launcher in System -> Preferences, I get this error:

"The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available. [OK]"


I've yet to try uninstalling kdm and dosbox.  I'm on a Thinkpad R60 with an ATI Radeon Mobility 1400, the fglrx drivers are installed.


Is there any way to do like a system rollback?

---

### Post by wardrich on 2008-10-25
I'm an idiot, lol.  Seems that something messed around with my xorg.conf.  I changed it from 800x600 to 1024x768.  Things seem fine now.

---

