---
title: "Dual Screen Issues"
date: 2009-11-06
forum: Hardware
---

### Post by cccc297 on 2009-11-06
I have a nVidia GeForce 7600 GT 256 MB Video Card with tho screens plugged into it and i trying to get nVidia DualView set up for them. I change the settings so they are in DualView mode but then on the next restart it goes back to my primary screen.

Thanks,
CCCC297

---

### Post by realzippy on 2009-11-06
edit settings with root privileges.

Terminal:

**gksudo nvidia-settings**


make settings,hit "apply",hit "save to x configuration file"  before exit nvidia-settings

if you get "parsing" warning,have a look here:
[http://ubuntuforums.org/showthread.php?t=1312435](http://ubuntuforums.org/showthread.php?t=1312435)

---

### Post by cccc297 on 2009-11-06
Thanks, I'll try that once I've gotten my other problem solved.

CCCC297

---

