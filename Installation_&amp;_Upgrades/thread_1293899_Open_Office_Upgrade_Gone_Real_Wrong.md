---
title: "Open Office Upgrade Gone Real Wrong"
date: 2009-10-17
forum: Installation &amp; Upgrades
---

### Post by GadeTerbob on 2009-10-17
Jaunty installed as dual boot.

Used synaptic to upgrade open office. Failed at first because it said files were open and to reboot. Rebooted, started update manager again, ran normal w/o error message and ended with note to reboot. Reboot fails with this error:

```
mountall: symbol lookup error: mountall: undefined symbol: udev_monitor_filter_add_match_subsystem_devtype
init: mountall main process (800) terminated with status 127
rm: cannot remove '/forcefsck': Read-only file system
init: mountall post-stop process (801) terminated with status 1
```

I'm at the point where I'm about ready to format the whole partition and start over. I've never fouled up a computer so bad that it couldn't be thrown away. :mad:

---

### Post by wilee-nilee on 2009-10-17
You might try this PPA,  [https://launchpad.net/~openoffice-pkgs/+archive/ppa](https://launchpad.net/~openoffice-pkgs/+archive/ppa)  It will overwrite and install, OO has some finicky actions if anything is not purged correctly.

---

### Post by GadeTerbob on 2009-10-18
Thanks! Worked great! Cheers!

---

