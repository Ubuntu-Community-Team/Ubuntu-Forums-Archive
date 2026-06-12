---
title: "xorg.conf corrupted?"
date: 2005-12-03
forum: General Help
---

### Post by Bolverk on 2005-12-03
I rebooted my laptop yesterday and when it was done rebooting, X wouldn't start. I chased down the error message and it said that there was an error in xorg.conf. I open up xorg.conf and the first 20 or so lines are loaded with control characters. I have a couple of backups in the X11 directory, but then I look and find xorg.conf.bak which was generated 2 hours before the reboot. I didn't make that backup file. I didn't do any upgrades / updates either. Very strange. I kept the corrupt file, and when I opened it up in kwrite, it complained that the corrupt xorg.conf file was a binary. 

[xorg.conf.WTF](http://www.jotunheim.net/linux/xorg.conf.WTF)

Any ideas?

---

### Post by mlomker on 2005-12-03
You can run **sudo dpkg-reconfigure xserver-xorg** to create a new one.

---

### Post by Bolverk on 2005-12-03
[QUOTE=mlomker]You can run **sudo dpkg-reconfigure xserver-xorg** to create a new one.[/QUOTE]

Oh, I fixed it in about 15 minutes. What I'd like to know is the *cause* of the corruption.

---

