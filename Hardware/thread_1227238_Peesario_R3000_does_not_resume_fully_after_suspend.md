---
title: "Peesario R3000 does not resume fully after suspend on 2.6.28-14 kernel"
date: 2009-07-30
forum: Hardware
---

### Post by Dakiraun on 2009-07-30
Hey gang.  After updating my R3000 to the 2.6.28-14 kernel, suspend (as well as hibernate) doesn't quite resume all the way.  The machine powers back up and the kern.log shows everything correctly, but it seems to stop at the last step where it should restore Gnome.  It dies there, showing only the Wallpaper background after I log back in.

No amount of waiting makes any difference.  I have to kill the X-session and re-log into GNOME via gdm, then all is working again.  This wasn't an issue until the recent kernel update.  Anyone have any ideas?  I could find no obvious errors in kern.log or messages.

---

### Post by Dakiraun on 2009-08-01
Update - this issue seems to be exclusive to the Gnome user profile.  I created a test user and tried suspend from it, and it worked fine.  I can also go into and out of suspend from the gdm login screen, and that works fine.  It's just my own profile that has something causing it not to resume correctly. I haven't figured out what the issue is.  Any ideas?

---

### Post by Dakiraun on 2009-08-18
Yet another update on this.  I tried a little troubleshooting to see if the inability to resume fully was based on a particular piece of Gnome, such as the panel.  I killed the gnome-panel process using vtty2 (which functions fine after the resume), but it had no affect.  I also tried killing the gnome-power thread with no luck.  

I see today that the 2.6.28-15 kernel is out, so maybe with luck the issue will go away after updating tonight.

---

