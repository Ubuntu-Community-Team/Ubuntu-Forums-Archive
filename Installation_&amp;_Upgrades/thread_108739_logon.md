---
title: "logon"
date: 2005-12-26
forum: Installation &amp; Upgrades
---

### Post by dog_soldier on 2005-12-26
when i boot the computer it gets as far as where it says logon then the screen goes black. is there a way to skip the logon?

---

### Post by cmcgeecc on 2005-12-26
well...it could be that your refresh rate isn't set to be compatible with your video card or monitor or your resolution is set too high.  In order to get into command prompt hit ctrl alt F1.  After you do that cd to /etc/X11 then edit the xorg.conf file.  You'll have to just figure it out by trial and error.  Research the type of monitor and video card you have to figure out what it can handle.  But before you start editing you should back up your file by typing cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
After you do that if you screw up you can just rm the xorg.conf file and rename the xorg.conf_backup file to xorg.conf if you screw something up.

---

