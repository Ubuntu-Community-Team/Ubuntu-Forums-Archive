---
title: "trouble suspending, hibernating, and restarting"
date: 2008-08-29
forum: Hardware
---

### Post by erinspice on 2008-08-29
I just installed Hardy on my HP 6113, and I'm having trouble suspending, hibernating, and restarting. Restarting only shuts down. My laptop never boots back up.  When I hibernate or suspend, I can't ever get it to wake up. The screen turns "on" but is black like the screensaver is on, but moving the mouse or pressing keys doesn't turn it back on.  This happens in dual and single monitor mode, but never affects my external monitor (which is my primary in dual mode). It only affects the laptop's monitor. Does anyone have any ideas or troubleshooting tips for me?

---

### Post by highlandsun on 2008-08-29
Sounds familiar. I'm chasing down a similar problem on my HP dv5z (except that restarts work fine for me). Suspend-to-RAM always hangs when trying to wake up, and only the power button gets any response. Mouse or keyboard doesn't do anything...

So far, no ideas. Tracking it here
[http://bugzilla.kernel.org/show_bug.cgi?id=11368](http://bugzilla.kernel.org/show_bug.cgi?id=11368)

Your situation isn't exactly the same, but may be closely related. You could try testing the 2.6.27-rc4 kernel to see if the situation has improved there. (It hasn't for me...)

---

