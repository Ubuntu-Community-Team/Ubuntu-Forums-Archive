---
title: "Need to rollback to the nouveau driver"
date: 2013-02-21
forum: Hardware
---

### Post by petezhut on 2013-02-21
I have tried for five days to get the nvidia drivers working for my GeForce GT 640M, and at this point I have managed to either get a 640x400 display or just a blank screen.  I have tried a myriad of methods to get the nvidia drivers to work, to no avail.  The system worked ok under the nouveau drivers; I just couldn't play any Steam games.  At this point, I just want to roll back to the nouveau drivers.  Can someone please help me to get the nouveau drivers working again?  I have uninstalled nvidia_current and nvidia_settings; but still no usuable screens.  Please, please help.

Thank you.

---

### Post by fuorviatos on 2013-02-21
Backup your /etc/X11/Xorg.conf file and remove it. Make also sure the nvidia kernel module is exluded from loading. 
You can also check if there are any nvidia packages left still in your system. Type:

> dpkg-l|grep 'nvidia' and look for any packages with the [ii] mark next to them.
When you remove your Xorg config file, your system should recreate it with the nouveau driver.

Good luck

---

