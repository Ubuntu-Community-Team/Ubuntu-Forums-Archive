---
title: "GRUB won't load...."
date: 2009-10-11
forum: Installation &amp; Upgrades
---

### Post by chintanjoshi on 2009-10-11
I have 2 500gb hdd....had installed ubuntu in the first one and then windows xp in the other.......as a result the one with ubuntu will not boot..........need solutions...

---

### Post by raymondh on 2009-10-12
> **chintanjoshi said:**
> I have 2 500gb hdd....had installed ubuntu in the first one and then windows xp in the other.......as a result the one with ubuntu will not boot..........need solutions...

-Any error messages? 
-In BIOS, which is the HD that is set to boot first?
-Where did you install GRUB?

Regards,

---

### Post by presence1960 on 2009-10-12
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

