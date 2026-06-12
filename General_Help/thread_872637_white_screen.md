---
title: "white screen"
date: 2008-07-28
forum: General Help
---

### Post by dish on 2008-07-28
I just upgraded from 7.10 to 8.04 and after I enable the nvidia driver for my nvidia 8600GT and restart, I get a sort of white screen where the login screen would have been, and I can't see my mouse pointer either.  Going in to recovery mode and fixing xorg.conf removes it, but the driver is disabled.  Any ideas why?

Thanks

---

### Post by overdrank on 2008-07-28
> **dish said:**
> I just upgraded from 7.10 to 8.04 and after I enable the nvidia driver for my nvidia 8600GT and restart, I get a sort of white screen where the login screen would have been, and I can't see my mouse pointer either.  Going in to recovery mode and fixing xorg.conf removes it, but the driver is disabled.  Any ideas why?

Thanks

Hi and welcome, If you enable the driver and the boot into recovery mode, you are using the xfix option? If so you may try and enable the driver and on reboot you receive the blank screen then try and use the alt, ctrl, F1 keys and this should bring you to the command prompt where you can try and reconfigure your xorg with this command. ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` the restart system with ```
sudo reboot
``` hope this helps.

---

### Post by dish on 2008-07-28
hmm that worked, but disabled the driver, and if I enable it again it does the same thing.  By the black screen do you mean after I run xfix or something?

---

### Post by overdrank on 2008-07-28
> **dish said:**
> hmm that worked, but disabled the driver, and if I enable it again it does the same thing.  By the black screen do you mean after I run xfix or something?

Ok if you have not tried the xfix option then you may, but I would suggest Envy to install the drivers. Hopefully Envy can help.

---

### Post by dish on 2008-07-28
ok I'll try envy now, and yeah I tried xfix before

envy worked! thanks!

---

