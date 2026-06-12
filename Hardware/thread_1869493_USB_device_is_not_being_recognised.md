---
title: "USB device is not being recognised"
date: 2011-10-25
forum: Hardware
---

### Post by TheFlamingFoot on 2011-10-25
USB hub attached to laptop, attached to that is a keyboard, mouse and webcam.

After using xubuntu for some duration, one of these will stop working. Eg. the mouse will stop moving the pointer (however it will still be powered - the red light still illuminates). Unplugging the USB hub and plugging it back in a different port does not resolve the issue.

The weirdest bit is that if I unplug all devices from the hub and plug them all back in one-by-one, the first device I reattach will be the one that does not work. :shock:

I've got no idea what's going on, nor where I should be looking for relevant logs etc :|

Any suggestions?

---

### Post by diasf on 2011-10-25
Does that happen on another pc?

---

### Post by Toz on 2011-10-25
In my experience, usb hubs come in varying levels of quality. The one I had a while ago had similar issues, and when I replaced it all was better. @diasf suggestion is a good one - do you have access to a windows box where you can test the hub? If you have similar problems there - it may be the hub.

Otherwise, the log file you probably want to review is /var/log/syslog. Running:
```
dmesg
``` in a terminal window may also yield some information.

---

### Post by TheFlamingFoot on 2011-11-01
I haven't responded because... well, suddenly it has started working and, as far as I know, I have changed nothing.

Weird.

Oh well, problem solved.

---

