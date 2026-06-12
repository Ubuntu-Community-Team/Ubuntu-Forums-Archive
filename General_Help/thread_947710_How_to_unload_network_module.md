---
title: "How to unload network module"
date: 2008-10-14
forum: General Help
---

### Post by olavjunior on 2008-10-14
I'm trying to work around the problem with n-networks in Intrepid ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276990)) compiling and installing a newer iwlagn module. But at the end of install it says I'm supposed to use "make unload", but that results in this output:

```
Unloading mac80211...
FATAL: Module mac80211 is in use.
Unloading cfg80211...
FATAL: Module cfg80211 is in use.
make: *** [unload] Error 1

```

How do I unload it???

---

### Post by boterbram on 2008-10-24
Same, please help

---

### Post by Yellow Pasque on 2008-10-24
Blacklist those modules and then restart your system.
```
gksudo gedit /etc/modprobe.d/blacklist
```

---

### Post by olavjunior on 2008-10-27
The old moduels are automatically replaced by the new ones after reboot in the case I was referring to, so no need to unload, just reboot.

---

### Post by dburnett77 on 2008-10-27
Perhaps you have won of the newer flashable ROM's for your network inter-face.

F10 is the func. key for my configuratoin..  Try a key, press

---

