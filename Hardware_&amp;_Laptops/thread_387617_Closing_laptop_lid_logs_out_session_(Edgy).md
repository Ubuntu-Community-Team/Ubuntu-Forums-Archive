---
title: "Closing laptop lid logs out session (Edgy)"
date: 2007-03-18
forum: Hardware &amp; Laptops
---

### Post by moephan on 2007-03-18
Hello,

Whenever I close the lid to my laptop, I am completely logged out of my session, and have to log back in. 

1. The power management applet appears to have no effect.
2. I read this thread: [http://ubuntuforums.org/showthread.php?t=378544&highlight=close+laptop]("http://ubuntuforums.org/showthread.php?t=378544&highlight=close+laptop")
and found that I can control the behavior by editing the /etc/acpi/events/lidbtn file and doing "sudo /etc/init.d/acpid restart". However, these changes are only effective until I restart Ubuntu, at which point it goes back to the logging me out behavior.

Any one know what else might be going on? Thanks.

Cheers, Rick

---

### Post by brettr on 2007-03-18
You might try and check out this post. [Force Monitor to turn on when lid open]("http://ubuntuforums.org/showthread.php?t=358432&highlight=lid.sh.pre")

It might lead you in the right direction, but it sounds like gdm/xorg is crashing when you close your lid. have you looked at /var/log.Xorg.0.log for any possible errors?

---

