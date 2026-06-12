---
title: "Mouse Cursor Lagging"
date: 2011-08-22
forum: Hardware
---

### Post by Monara on 2011-08-22
Dear Ubuntu forums,

I have a Dell Studio 15 laptop that dual boots 11.04 and Windows 7 with a Phillips optical mouse. The cursor occasionally becomes non-responsive and I'm baffled as to why that would happen. Is it a problem with Ubuntu, a hardware conflict, or do I have a malfunctioning mouse?

---

### Post by sbraz on 2011-08-22
does your touchpad work okay when the mouse is unplugged?

please post the output of this command:
```
uname -a
```

---

### Post by Monara on 2011-08-22
I do not often use touchpad, but when I do, I never seem to notice this problem.

The output of uname -a was:
Linux GLaDOS 2.6.38-11-generic #48-Ubuntu SMP Fri Jul 29 19:02:55 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by sbraz on 2011-08-22
if the touchpad works fine it's the mouse;
if your mouse works fine in windows but not in linux there's a problem between linux and that particular mouse.

please post the output of this other command (leave your mouse connected):
```
lsusb
```

---

### Post by Monara on 2011-08-22
The output is: 
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 006: ID 1c4f:0003 SiGma Micro HID controller
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1058:0704 Western Digital Technologies, Inc. Passport External HDD
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0c45:63ea Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by Monara on 2011-08-23
Switching to a different mouse seems to have solved the problem.

---

