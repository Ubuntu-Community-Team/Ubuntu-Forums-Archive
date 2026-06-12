---
title: "Latitude D600 won't wake from sleep"
date: 2010-05-27
forum: Hardware
---

### Post by oiler920 on 2010-05-27
Just installed Lucid Lynx on my Dell Latitude D600 and discovered that it will no longer wake from sleep. It goes to sleep fine when I close the lid, but when I open it back up, it stays on a black screen, and I have to shut it off by the power button. 9.10 Karmic worked fine, so there's a regression somewhere. Is anyone having a similar issue?

---

### Post by grapedaddy on 2010-05-28
same problem --same laptop
 
Here is one of the bug reports for you to join:
 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/559163](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/559163)
 
I'm using hibernate instead of suspend. That works most-of-the-time. When it fails to hibernate, it overheats with the lid closed because it is still running.

---

