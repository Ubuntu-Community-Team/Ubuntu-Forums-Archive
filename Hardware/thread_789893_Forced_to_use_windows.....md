---
title: "Forced to use windows...."
date: 2008-05-10
forum: Hardware
---

### Post by Ryupower on 2008-05-10
Otherwise I couldn't post this. :(
I did an update today via update manager. It rebooted, and now my wireless isn't working on ubuntu. I've been trying to get it to work again, but I seem to not be able to.
Anyone know how to fix this? 

Intelpro Wireless 2200 on Ubuntu Hardy Haron.

---

### Post by EXCiD3 on 2008-05-11
Did you update to a new kernel version? That could have broken your wireless.

Same issue has been reported on launchpad. You should also comment on that bug.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210595](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/210595)

---

### Post by Ryupower on 2008-05-11
wow. the EXACT same problem. Thank you for your response!

---

### Post by HunterThomson on 2008-05-11
Can you just choose to but up the old kernel in grub? I don't have this problem I was just wondering and it would help them too....

---

### Post by EXCiD3 on 2008-05-11
> **HunterThomson said:**
> Can you just choose to but up the old kernel in grub? I don't have this problem I was just wondering and it would help them too....

That should work fine temporarily until they get the drivers working with the new kernel. You should try this tutorial however switching the iwl3945 to the intel 2200 driver, ipw2200.

---

