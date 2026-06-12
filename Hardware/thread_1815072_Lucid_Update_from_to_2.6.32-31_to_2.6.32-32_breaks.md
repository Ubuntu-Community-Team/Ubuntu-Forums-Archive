---
title: "Lucid: Update from to 2.6.32-31 to 2.6.32-32 breaks suspend mode"
date: 2011-07-30
forum: Hardware
---

### Post by ujay68 on 2011-07-30
Hi, after the update of 10.04.3 from kernel 2.6.32-31 to 2.6.32-32 (x86/32-bit), I can no longer use the suspend mode on a ThinkPad T500. The suspend LED (moon symbol) blinks indefinitely, and I have to use the hard switch-off and reboot. The problem remains with 2.6.32-33. When I boot the older 2.6.32-31 kernel, everthing works fine. Anyone else having this problem? Cheers, Jay

---

### Post by mnttnlyzr on 2011-08-01
Mine's broken too. R400.

---

### Post by Forecast on 2011-08-02
Same here on an R500.

---

### Post by ujay68 on 2011-08-03
Filed a bug report at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/820269](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/820269)

---

### Post by Forecast on 2011-08-03
I retried suspend with 2.6.32-32 and it worked. It rather seems to break for me from 2.6.32-32 to 2.6.32-33.

---

