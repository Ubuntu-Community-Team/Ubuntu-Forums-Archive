---
title: "After resuming from suspend, special keys on top row are locked to F1-F12"
date: 2024-09-08
forum: Hardware
---

### Post by howardcheng2 on 2024-09-08
I have an MSI laptop and the top row of its keyboard has the function keys F1-F12 that are normally mute, vol-, vol+, touchpad on/off, etc.  If I wanted to use the function key, I would have to press "fn" in addition to the top row key, which is expected.

If I suspend my laptop and resume, the keys in the top row are now locked to F1-F12 and I cannot get them to be used as mute, vol-, vol+, etc. at all.

I have tried using xev to see what events are generated.  Before suspend/resume, I will not get any keypress event when I hit those keys without "fn", and events for F1, F2, etc. with "fn".  After resume, I only get events for F1, F2, ... with or without fn pressed.  I have also toggle fn lock (fn + Esc) and that made no difference.  The only thing that resets the behaviour appears to be a reboot.  Logging out and logging back in doesn't help either.

Any ideas?

---

