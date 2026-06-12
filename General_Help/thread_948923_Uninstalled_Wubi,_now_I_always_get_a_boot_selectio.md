---
title: "Uninstalled Wubi, now I always get a boot selection screen when starting"
date: 2008-10-15
forum: General Help
---

### Post by Sequestered on 2008-10-15
Greetings. I recently uninstalled Wubi because Ubuntu would not properly start, and because I lost interest in installing Ubuntu on this computer. After uninstalling Wubi, I still get a boot selection black-and-white screen when I turn on my computer. It lets me choose my Windows XP or a Recovery Console. However, before installing Wubi, I never had a boot selection screen. 

Not only do I have this problem now, but I also can't access my System Restore option. Normally when my computer started, I could enter an interface that would allow me to restore my Windows to factory mode.

I would greatly appreciate any help on how to remove the boot selection, which may perhaps allow me to enter System Restore.

---

### Post by Orlsend on 2008-10-16
Here is the Solution:

***"In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line. For Vista, you can use EasyBCD to edit the boot menu"***

---

