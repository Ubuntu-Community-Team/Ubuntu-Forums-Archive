---
title: "Still asks which OS to boot with ubuntu uninstalled"
date: 2009-07-20
forum: Installation &amp; Upgrades
---

### Post by sehana on 2009-07-20
Ok so I installed ubuntu using the install/uninstall option and I liked ubuntu, but I will wait to install fully when hard drive arrives. 

So I uninstalled it and restarted PC.

At Boot it still asks whether I want to install XP or Ubuntu.
How to get rid of that?

---

### Post by raymondh on 2009-07-20
> **sehana said:**
> Ok so I installed ubuntu using the install/uninstall option and I liked ubuntu, but I will wait to install fully when hard drive arrives. 

So I uninstalled it and restarted PC.

At Boot it still asks whether I want to install XP or Ubuntu.
How to get rid of that?


Hello Sehana,

For WUBI installs ..... You need to access the boot.ini files of windows and edit/remove ubuntu related lines.  

WARNING : edit/remove **JUST** the UBUNTU-related lines.

From the [wubiguide]("https://wiki.ubuntu.com/WubiGuide") wiki:

[I]How do I manually uninstall Wubi?

Remove C:\ubuntu and C:\wubildr*.

In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line. For Vista, you can use EasyBCD to edit the boot menu. Alternatively you can modify the boot menu via control_panel > system > advanced > startup_and_recovery and pressing "Edit". For Windows 98 you have to edit C:\config.sys, and remove the Wubi block.[/I]

If unsure, post back for more assitance.

Regards.

---

### Post by sehana on 2009-07-20
Thanks that worked

---

### Post by /usr/sbin on 2009-07-20
Thanks Raymond

---

### Post by raymondh on 2009-07-20
You're both welcome.

Happy Ubuntu-ing :)

Best,

---

