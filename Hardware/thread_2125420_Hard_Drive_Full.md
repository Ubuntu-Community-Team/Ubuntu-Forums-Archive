---
title: "Hard Drive Full"
date: 2013-03-13
forum: Hardware
---

### Post by RyeMan on 2013-03-13
My lubuntu 12.04 system will not boot because the HD is completely full.  Tried live disk of same version but it will not let me delete  or move any files because of permissions.  If I try to change the permissions it will not let me do that either.  Can you tell me how to remove a file to get room or to change the permission?

---

### Post by papibe on 2013-03-13
Hi RyeMan.

You should be access your hard drive with root privileges by using the Live CD. Remember that you have to use 'sudo' or 'gksudo' nevertheless.

Regards.

---

### Post by typhoon_tip on 2013-03-14
Not necessary to use liveCD. Press SHIFT while booting at the very beginning, you will be presented with GRUB boot menu. Select the latest kernel in "recovery" mode, it will boot and present you with a series of option. I am not sure which one exactly, but there's one that does some "clean up", cleaning packages and temp files, recovering usually enough space to allow a normal boot. After that, login and perform a more detailed cleanup with usual apps.

---

### Post by RyeMan on 2013-03-14
Worked perfectly...much thanks!

---

