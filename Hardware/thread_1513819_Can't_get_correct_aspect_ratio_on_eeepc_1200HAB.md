---
title: "Can't get correct aspect ratio on eeepc 1200HAB"
date: 2010-06-20
forum: Hardware
---

### Post by massasauga on 2010-06-20
The monitor on my eeepc 1200HAB is proportioned to an  a approximate 16:9 or 16:10 ratio. No matter what I do to the configuration it stays set to a 4:3 ratio, but it is stretched across the 16:9 screen. In other words, if I display a photo on the screen, everyone looks fat. I suspect I need to install a different video driver. I have tried running the command:
 Xorg -configure
The resulting xorg.conf file ("xorg.conf.new", which I copy into "/etc/X11/xorg.conf" ) tries to install a driver called "fbdev", but the video doesn't work at all unless I comment out the driver in xorg.conf and replace it with "vesa". I set the modes to "1024x600" in the Screen section in each "Display" subsection. 

I am running Ubuntu 10.04.

Does anybody know how to get this to work correctly? Thanx.

Regards,

--Gregg

---

