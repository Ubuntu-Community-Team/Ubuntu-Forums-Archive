---
title: "How can I disable &quot;Clickpad&quot; mode in the Synaptics driver?"
date: 2010-10-22
forum: Hardware
---

### Post by mosquitogang201 on 2010-10-22
So I just upgraded to 10.10 on my Inspiron 1520 laptop. The bottom portion of my touchpad is no longer working. Apparently "Clickpad" mode has been enabled in the Synaptics driver for my touchpad - I do not have a Clickpad, I have physical mouse buttons on my laptop. Is there any way to disable this mode so I can use my entire touchpad again?

---

### Post by MataS-nl on 2010-10-26
I'm having the same problem. But not only the bottom part of my touchpad is not working, the middle (physical) mouse button below my touchpad is reported as a left mouse button. When I press the middle mouse button, xev and evtest report it as a left mouse click.

My touchpad worked well in 10.04, the difference in dmesg is this line:
```
[   14.945225] Synaptics: Clickpad mode enabled
```

My best guess is to turn of the clicpad mode: any ideas?

---

### Post by MataS-nl on 2010-10-27
After searching some more I found this bug report: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/612591](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/612591)
The fix mentioned here in reply #11 works for me.

---

