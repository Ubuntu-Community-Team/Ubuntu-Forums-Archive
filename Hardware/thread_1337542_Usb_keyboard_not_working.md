---
title: "Usb keyboard not working"
date: 2009-11-25
forum: Hardware
---

### Post by sandos on 2009-11-25
My Microsoft Natural Ergonomic Keyboard 4000 randomly stops working when I re-plug it after using it in my laptop. This is severely annoying, understandably, since only a reboot solves the problem!


This did not happen on jaunty, and seems a recent problem on karmic. Restarting udev does not help. Any ideas?

---

### Post by Felson on 2009-11-25
try restarting HAL instead.
```

sudo restart hal

```

---

### Post by sandos on 2009-11-26
Thanks, I will try that next time it happens! I actually tried a suspend-resume cycle as well, but that did not help!

---

### Post by kh1116 on 2009-12-01
I'm experiencing similar problems:
[http://http://ubuntuforums.org/showthread.php?t=1343473]("http://http://ubuntuforums.org/showthread.php?t=1343473")

---

