---
title: "Nvidia settings"
date: 2010-10-10
forum: Hardware
---

### Post by doyleman on 2010-10-10
I just got a new 24 inch monitor, and the current nvidia drivers aren't playing nice with it. Originally, it would auto set the resolution to some other than 1920x1080 (its default optimal max). finally, after searching, i found that by clicking the system > monitor then clicking no on default setting manager, it'd stay.

This works nice enough for me, but the Login screen is all wacked out now. It can pan in directions, and isnt showing the entire Login Screen. Sometimes I have to pan my mouse around to find the password input field.

anyone know how i can fix this?

---

### Post by doyleman on 2010-10-11
bump

---

### Post by doyleman on 2010-10-11
bump again.

---

### Post by efflandt on 2010-10-11
You have not said which Ubuntu version, which video card/chip, and which nvidia driver version.  For example some older chips might actually be running nvidia version 96 or 173 instead of the newest version (which is different in 10.10 vs. 10.04 or older Ubuntu versions).  Also if connected with VGA, the system is less likely to be able to determine details about your display than DVI or HDMI.

I am connected DVI to HDMI to a 1080p HDTV and things before gui login including splash or plymouth are a lower resolution and/or underscanned (shrunken) with the nvidia driver.  But gui login and X are 1920x1080.  The default nouveau driver boots full screen even for plymouth, but is less than 1/10th as fast.

But it sounds like either you are not using the proprietary nvidia divers, or they are not working for you. if you can go to System > Preferences > Monitors which tells me:

> It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?For proprietary nvidia drivers the vender's tool would be System > Administration > NVIDIA X Server Settings.  If you do not see that, you might be using the default nouveau drivers instead of actual nvidia drivers.

---

### Post by doyleman on 2010-10-11
Apologies for the lack of info. I am using the nvidia drivers, in Ubuntu 10.10, and with the Nvidia PNY Geforce 9400 GT, using version 260.19.06.

---

### Post by efflandt on 2010-10-11
That is the nvidia version I am using (for a GT 220).  But I never have been able to figure out how to set any resolution before you have logged into X.

Settings you make from NVIDIA X Server Settings are stored in your own ~/.nvidia-settings-rc which do not take effect until you login.  Maybe someone more familiar with xorg.conf could tell you what to plug into /etc/X11/xorg.conf.

---

### Post by doyleman on 2010-10-12
well, knowing i should edit xorg.conf is a big stride forward, for me. thanks :D

---

