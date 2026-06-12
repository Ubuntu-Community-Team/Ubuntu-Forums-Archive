---
title: "new Jaunty on old box -- how to configure monitor?"
date: 2009-07-01
forum: Hardware
---

### Post by 4dummies on 2009-07-01
I've got this 10-year-old box with a somewhat newer Xerox XL370B monitor.  I just installed Jaunty on it, and it works but is only willing to give me 600x800 resolution on the screen because Xorg is using default refresh rates.  These are 31.50-37.90 kHz and 50-70 Hz.

I can't find a manual for the monitor it in my cabinets or online.
Windows XP runs it at 1280x1024 and four other resolutions down to 800x600.

With the new Xorg, I'm not even sure where these specs should go.

Anybody want to help me guesstimate the refresh rates proper to such a monitor?  And give me a sample xorg.conf file to get this working right?

---

### Post by 4dummies on 2009-07-06
Update: using
   Xorg -configure
I got up to 1024x768 resolution, which looks squashed on this monitor (fonts look skinny), but even trying the things in the old xorg.conf from before the upgrade, I have not found a modeline that gets the native 1280x1024, which is what I was used to.

Where does one go for help tweaking an xorg.conf?

++ kevin

---

