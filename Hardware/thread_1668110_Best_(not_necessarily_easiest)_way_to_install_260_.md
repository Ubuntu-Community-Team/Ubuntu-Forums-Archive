---
title: "Best (not necessarily easiest) way to install 260 Nvidia drivers?"
date: 2011-01-15
forum: Hardware
---

### Post by Harry Muscle on 2011-01-15
I've upgraded my machine's graphics card to a NVidia GTS450, unfortunately Ubuntu doesn't have any "restricted" drivers that work for this card, so I need to find an alternate way to get the driver installed.  I've tried the drivers from the ubuntu-x-swat PPA repository, but for some reason they won't work for me.  When I restart the X server, I'm still stuck with no drivers (and low resolution).  If I run nvidia-xconfig to created a xorg.conf file to force usage of the drivers, I just get a failed X start up with the option to modify graphics settings, etc.  Then I tried to manually install the drivers from the NVidia website, they actually work (once a xorg.conf file is created), but I'm concerned about what will happen when a new kernel is installed.  Will I have to reinstall the drivers manually every time a new kernel comes out?  I really would prefer to stick to a packaged version of the 260 drivers just to avoid any issues with the NVidia installer (which I read is not 100% reliable all the time).  Are there any other repositories that I can check out for the drivers?

Thanks,
Harry

P.S. I've done a lot of the testing using the Live CD so I don't mess up my system, but I doubt that makes any difference.

---

