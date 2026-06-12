---
title: "Ubuntu tries to access the DVD drive"
date: 2017-04-16
forum: Hardware
---

### Post by coverup1128 on 2017-04-16
Time to time, my Ubuntu 14.04 laptop tries to access the DVD drive. The tray is empty, and I cannot see any reason for the system to try to mount the drive. It's not a big issue but is somewhat annoying that I cannot find what is causing it. Besides, this probably draws some power, which is undesirable. I don't recall any older Ubuntu or other distros behaving this way. Has anybody observed a similar behaviour? What could be causing it?

---

### Post by gsahli on 2017-04-17
It may be a hardware issue - the door position sensor, for example. Does the command "eject -t" return any error?

---

### Post by coverup1128 on 2017-04-18
Yes indeed, I get an error:

```
$ eject -t
eject: CD-ROM tray close command failed: Input/output error
```

If I only knew what is causing it!

---

### Post by gsahli on 2017-04-19
CD/DVD drives fail all the time - because of moving parts and exposure to the outside.

---

