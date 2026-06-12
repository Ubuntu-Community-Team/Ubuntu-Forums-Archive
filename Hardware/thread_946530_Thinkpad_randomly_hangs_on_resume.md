---
title: "Thinkpad randomly hangs on resume"
date: 2008-10-13
forum: Hardware
---

### Post by W. Irving on 2008-10-13
My T23 sometimes will not resume properly from hibernation on Ubuntu 8.04. Two out of five times, the laptop hangs in one way or the other. Either the screen remains black no matter which key I press (backlight off as well), or upon moving the cursor or pressing a key, the computer reacts and displays the unlock session box - only to hang right away.

When it's in this frozen state, the fan still occasionally runs, but the network is presumably down (VNC, Samba, and Apache are unresponsive).
I've compared syslogs between a successful resume and one that hangs, and they look the same. The last line seems to be this:
```
kernel: [   60.338941] eth0: no IPv6 routers present
```
although sometimes cron does something a minute later..

The screen displays a pattern of vertical green lines on hibernation, but it always powers off correctly. I tried disabling ACPI (using the acpi=off kernel switch), but the only difference was that suspend was no longer available, and it wouldn't power off automatically when hibernating. Resume was still unpredictable, so I don't believe this is a problem with ACPI at all.

Does anyone have a clue as to what's causing this annoying problem, or know how I can further troubleshoot?

**EDIT**
After doing a few tests, I think it's safe to say now that it's the port replicator that messes up the resume process. If it's connected at resume time, there's a very slim chance the laptop will come to life again after hibernating/being suspended. Still, the syslog gives no hint about this, though I haven't changed the debug level yet. Consider this a FYI.

**EDIT 2**
Laptop froze this morning upon resuming, and the port replicator was not plugged in at the time, so this issue is still very much valid.

---

### Post by cl0ckwork on 2008-10-13
unfortunately, this is the bane of most computers running linux.

suspend and hibernate rarely work correctly unless you built the kernel yourself from scratch

---

### Post by W. Irving on 2008-10-13
Yup, I've noticed it with older versions of Ubuntu too, but hibernation in 7.10 worked well. You seem like a knowledgable person though - perhaps you know of a module or two known to cause problems?

---

