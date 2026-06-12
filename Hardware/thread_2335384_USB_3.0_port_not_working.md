---
title: "USB 3.0 port not working?"
date: 2016-08-28
forum: Hardware
---

### Post by SnazzleLabsYT on 2016-08-28
Hello everyone.

I'm running Kubuntu 16.04.1, fresh install. My computer has a USB 3.0 port and when a 3.0 drive is plugged into that port, it does not work.
Plugging a 2.0 drive in to the 3.0 port works.

Can someone help me?

---

### Post by TheFu on 2016-08-28
Are the chips inside the USB3 adapter supported by the kernel?  Is the USB3 device compatible with those chips?
Not all USB3 storage devices work with non-Windows platforms. Sad but true.

So, start by looking at all the log files - is the USB3 device recognized in a way similar to the USB2 devices that work?

Commands to use are:
```
lspci
lsusb
tail -f /var/log/syslog

```

---

### Post by SnazzleLabsYT on 2016-08-28
Well... Can a mod delete this useless thread?

Although rebooting before did not fix the issue, doing a reboot right now actually got the 3.0 drive to work..

I feel foolish.. :P

Thank you, TheFu.

---

### Post by TheFu on 2016-08-28
a) we've all done something similar. No issue with that.  Once had all the video go out. Tried multiple different inputs - 1 that was working 30 min earlier.  Swapped HDMI cables - twice. Tried all the inputs again.  Figured the DVD player was broke.  Then noticed that a connection to an HDMI replicator was loose. THAT was the issue. ... this was yesterday. ;)

b) in theory, a 2nd reboot shouldn't matter. I'd watch it closely for a few weeks and check post-reboot.

Hardly a useless thread. There is wisdom in each post.

---

