---
title: "Encrypted LVM stopped booting"
date: 2008-09-02
forum: General Help
---

### Post by 89vision on 2008-09-02
My system is setup with encrypted LVM.  Everything was working great until the other day when I rebooted after synaptics installed some updates.  Now whenever I turn the system on it hangs on the Ubuntu splash screen for several minutes then gives me the following message and drops to a initramfs shell.

```
Starting up ...
Loading, please wait...
    check root= bootarg cat /proc/cmdline
    or missing modules, devices: cat /proc/modules ls /dev
 Reading all physical volumes.  This may take a while...
ALERT! /dev/mapper/lappy-root does not exist. Dropping to a shell! 
```

I know all my data is still there on my root directory because I can mount it using the "rescue a broken system" option on the Ubuntu alternate install cd but I can't get it to boot.  I'm fairly linux proficient but I'm new to encryption and LVM.  Does anybody have any ideas?

---

