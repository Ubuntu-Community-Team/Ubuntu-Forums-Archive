---
title: "Remove ATI FGLRX driver from Ubuntu 11.04"
date: 2011-05-15
forum: Hardware
---

### Post by joshuaar on 2011-05-15
I recently installed Ubuntu 11.04 on an HP DV6 with switchable graphics (Intel shared graphics + ATI Mobility Radeon). On installation I installed the proprietary ATI/AMD FGLRX driver, but it does not seem to be functioning properly. I cannot access catalyst control center, or deactivate the driver from System > Administration > Additional Drivers. I also tried uninstalling via aticonfig --uninstall. I get the following error: 

"Uninstaller for ATI Catalyst (TM) Proprietary Driver, /usr/share/ati/amd-uninstall.sh, does not exist or cannot be found."

/usr/share/ati does exist, but it doesn't contain the uninstaller.

Ideally I would like to just shut off the ATI GPU, remove all remnants of its driver and run on the power saving Intel. The fact that the computer is running hot leads me to believe the ATI GPU is on but I'm not getting any graphics acceleration (Unity doesn't work). Other than these problems (running hot, excessive power use with no acceleration, inability to remove proprietary drivers), display seems to be functioning.

Let me know if I've given enough info, I'm new to Ubuntu, especially on the laptop.

---

### Post by joshuaar on 2011-05-15
I found the answer (sort of).  I removed the drivers and Unity works now, but I still don't know which GPU I'm using or if switchable graphics are even possible. Here's where I found the solution:

[http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

