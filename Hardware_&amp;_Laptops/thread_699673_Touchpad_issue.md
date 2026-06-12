---
title: "Touchpad issue"
date: 2008-02-17
forum: Hardware &amp; Laptops
---

### Post by Chris H on 2008-02-17
Anyone got any ideas on this?

At some point after logging in my touchpad will lose scroll ability and become very sensitive. All fixed when I log in and out but the problem always returns.Can occur anytime, sometimes doesn't happen all day, most times within 30 minutes of logging in though. 

This happens on virtually all distros with this laptop except openSuse (rarely) and Linspire. All desktops and window managers as well.

Touchpad is synaptics. The only reference I can find to it in the logs is this from syslog

> 
Feb 17 09:10:52 crossfire2 kernel: [ 5708.828000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 17 09:10:52 crossfire2 kernel: [ 5708.832000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 17 09:10:52 crossfire2 kernel: [ 5708.832000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 17 09:10:52 crossfire2 kernel: [ 5708.836000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 17 09:10:52 crossfire2 kernel: [ 5708.836000] psmouse.c: TouchPad at isa0060/serio2/input0 lost sync at byte 1
Feb 17 09:10:52 crossfire2 kernel: [ 5708.836000] psmouse.c: issuing reconnect request



Anyone?

---

### Post by Chris H on 2008-02-17
Some sites have suggested adding i8042.nomux=1 to grub so I'll see how that goes.

---

### Post by Chris H on 2008-02-18
24 hours later and all is well!

I know some other posters on these forums have this issue so maybe this will help someone out.

---

