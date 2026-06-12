---
title: "After first suspend, laptop forgets how to use lid switch?"
date: 2007-09-02
forum: Hardware &amp; Laptops
---

### Post by hardyn on 2007-09-02
With an Asus z71vp, after fresh reboot, the laptop suspends just fine after closing lid;  if the system is resumed and and the lid closed again the system will not suspend.

the system does suspend using the fn+f1 (suspend key combination)

thanks.

---

### Post by hardyn on 2007-09-03
bump

---

### Post by flamacue on 2007-09-06
[http://ubuntuforums.org/showthread.php?t=406250](http://ubuntuforums.org/showthread.php?t=406250)

That thread acknowledges the issue, and has an ugly workaround.  I won't use it personally, since it seems like a race condition to me.

Until the issue is fixed, I am just pushing and releasing the lid button before I close the lid--that's my workaround.

The bug is reported here:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34389](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/34389)

---

