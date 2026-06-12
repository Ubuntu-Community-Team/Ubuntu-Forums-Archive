---
title: "ok, this is the last straw"
date: 2010-03-10
forum: Hardware
---

### Post by nerdy_kid on 2010-03-10
been having suspend issues with my geforce 8600M every since i upgraded to karmic -- not the drivers as they worked fine in jaunty.  dont want to downgrade as it is a pain in the butt and i want KDE 4.4 which isnt around for jaunty.  X will crash randomly on resume with 
```

nvLock: client timed out, taking the lock
 ddxSigGiveUp: Closing log

```
in my kdm log.

I can only say that it usually happens when my battery is low.  (thought it was powermizer so i disabled the freq gov but to no avail)


anything, ANYTHING to help would be GREATLY HELPFUL

should i change kernel startup vars maybe, or tweak some scripts i really dont care just someone please give me some ideas at least!

---

### Post by nerdy_kid on 2010-03-10
i have googled for hours on this

---

### Post by nerdy_kid on 2010-03-11
bump.  come on people this is a show stopper!

---

### Post by nerdy_kid on 2010-03-12
this is really really wierd, apparently it doesn't effect GNOME.  what the heck?  time to tweak PowerDevil i guess.

---

### Post by nerdy_kid on 2010-03-12
think i got it.  apparently when the power profile turns compositing off, and then i suspend it, X crashes.  It actually crashes in the middle of suspending.  If I manually turn compositing off, then suspend.  no crash.

To reproduce on my machine:
drain battery to ~%5.
turn power profile to "Xtreme Powersave"
Click battery applet, suspend.
crash.

---

