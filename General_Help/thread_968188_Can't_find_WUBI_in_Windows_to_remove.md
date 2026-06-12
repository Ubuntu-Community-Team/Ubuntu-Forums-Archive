---
title: "Can't find WUBI in Windows to remove"
date: 2008-11-02
forum: General Help
---

### Post by Maynardk on 2008-11-02
Sorry if this is the wrong place to post but I am a newbie.  I installed 8.10 using WUBI on my Vista system.  Seemed to go ok but when it rebooted Vista said there was an error and it restored to a previous workable state.  On next reboot I got a windows startup menu listing Ubuntu and Vista.  Both start ok and seem to run ok.  Only problem is I would like to remove Ubuntu but can find it or Wubi listed under programs to remove.
maynardk:KS

---

### Post by AlucardNoir on 2008-11-02
try Ubuntu in place of Wubi.

---

### Post by Yownanymous on 2008-11-02
Or you could just run the installer again, which will prompt you to remove it.

---

### Post by Maynardk on 2008-11-02
Ubuntu not listed either, but thanks.  I will try other suggestion of running the installer again.

---

### Post by Maynardk on 2008-11-02
Thanks, I'll try that later.

---

### Post by ago on 2008-11-03
Not sure what happened when you went through a restore point, but see the wubi guide for manual uninstallation instructions. In particular, use EasyBCD to the edit the vista boot menu.

---

### Post by SerenityKill3r on 2008-11-03
Yeah, I'd just delete the ubuntu folder, and then use EasyBCD to remove the boot entry. Personally I'd run CCleaner afterwards to delete any obsolete registry entries :)

---

### Post by Maynardk on 2008-11-04
Thanks.  That seemed to work fine.  I deleted, used EasyBCD and followed up with CCleaner.  Appreciate the help.

---

