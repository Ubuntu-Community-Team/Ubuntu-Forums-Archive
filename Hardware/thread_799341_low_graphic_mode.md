---
title: "low graphic mode"
date: 2008-05-18
forum: Hardware
---

### Post by puma1017 on 2008-05-18
I just downloaded hardy and it was running fine, but the next time I rebooted, it said it was in low graphics mode. I have a Dell dv6500 with an Intel graphics card. My resolution is stuck in 600x800 when I try to configure it upon rebooting and it doesn't offer me a higher resolution. I downloaded start-up manager and changed it to a higher resolution, but it still boots in low graphics mode. I also tried git-clone git://anongit.freedesktop.org/git/xorg/driver/xf86-video-intel to no avail. Any suggestions? Also, I don't do too many video related things on my laptop besides the occasional movie, so would it be bad to always just run in low graphics mode?

---

### Post by pietjanjaap on 2008-05-19
Reboot to safe mode, choose the last one. This looks for hardware, your videcard and monitor.

Then reboot, and install your video driver.
(i do this with envy, in ubuntu)
Look also on the envy site for the textmode commands, these are very usefull.

---

### Post by dmurphy787 on 2010-08-16
Hoe do I reboot in safe mode please?

---

