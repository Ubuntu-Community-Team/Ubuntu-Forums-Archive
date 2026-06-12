---
title: "Uninstalling the &quot;Install inside Windows&quot; option."
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by Alterah on 2009-06-23
Hello,

I installed Ubuntu on my computer using the "Install inside Windows" option. I have recently uninstalled it and will try Ubuntu out when I build my next computer or get another hard drive. Anyhow, I noticed that during the boot cycle it still brings up a menu to select Windows XP or Ubuntu. I am just wondering how I can get rid of the Ubuntu choice so that my computer will just automatically boot into Windows. Thanks in advance.

---

### Post by anystupidname on 2009-06-23
Remove the Ubuntu line from c:\boot.ini using your favorite text editor.

If that wasn't removed, perhaps the uninstaller failed to remove the folder containing Ubuntu too. Check for an ubuntu folder in the root of C:

---

### Post by presence1960 on 2009-06-23
Control Panel > System > Advanced tab > Startup & Recovery options > click Edit. This will bring up boot.ini
Remove the line referring to wubi/Ubuntu **_ONLY_**
see this thread if unsure: [http://ubuntuforums.org/showthread.php?p=7501325#post7501325](http://ubuntuforums.org/showthread.php?p=7501325#post7501325)

---

