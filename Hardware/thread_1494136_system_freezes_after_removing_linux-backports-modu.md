---
title: "system freezes after removing linux-backports-modules"
date: 2010-05-26
forum: Hardware
---

### Post by ace95 on 2010-05-26
[SIZE=2]After upgrading to karmic from jaunty[/SIZE], I had a problem with broadcom STA wireless driver so I had to uninstall linux-backports-modules-2.6.31-21-generic after doing so my system freezes for no reason!and after reinstalling it, the system is ok again.any idea?

---

### Post by lidex on 2010-05-26
Try using synaptic to remove it first and before closing select your kernel there for re-installation and apply. Reboot.

---

### Post by ace95 on 2010-05-27
I fixed it:
first i uninstalled it:
```
$sudo aptitude remove linux-backports-modules-`uname -r`
```then rebooted and went to recovery mode.
there:
```
#depmod -a
#aptitude install linux-backports-modules-`uname -r`
#reboot
```then the wireless indicator light is turned on and in hardware drivers it says:(for broacom STA driver)
"This driver is activated and in use"
:popcorn:

---

