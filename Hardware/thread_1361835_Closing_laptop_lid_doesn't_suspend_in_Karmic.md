---
title: "Closing laptop lid doesn't suspend in Karmic"
date: 2009-12-22
forum: Hardware
---

### Post by ScottMinster on 2009-12-22
I'm not sure if there's really an answer to this question.  Maybe someone can point me to a relevant bug report that I can watch.  I've searched the forums and bug reports, but haven't found anything similar yet.

This problem started since I upgraded to Karmic.  In older versions, when I shut the laptop lid when on battery power, the laptop would suspend (per my gnome-power-manager settings).  When on AC power, it would just blank the screen.

Since Karmic, when I shut the lid on battery power, it just blanks the screen, it doesn't suspend.  However, if I manually suspend it (using the username menu applet), close the lid, open the lid to resume, then shut the lid, it does suspend correctly.  It's only the first time that I want to suspend that I have to manually do it.  After that, it works as expected.

It seems like maybe GPM isn't recognizing that it's on battery power.  It may be related to bug 444881 (no remaining time in power monitor), which does affect me.

Anyone have any ideas?  Or should I go make a bug report for it?

---

