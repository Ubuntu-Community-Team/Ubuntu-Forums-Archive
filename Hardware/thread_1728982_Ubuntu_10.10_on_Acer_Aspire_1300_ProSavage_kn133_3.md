---
title: "Ubuntu 10.10 on Acer Aspire 1300 ProSavage kn133 3d graphics not working"
date: 2011-04-14
forum: Hardware
---

### Post by sebbo90 on 2011-04-14
Installed ubuntu 10.10 on Acer Aspire 10.10 an everything installed perfectly and worked better than expected considering the age of the laptop. The only thing I cant seem to get to work is the 3d graphics. Accordng to the ubuntu onlne man pages the ProSavage kn133 (basically a savage4) should work for both 3d and 2d. However when I run glxears the screen goes black and logs me out. It just seems odd as direct rendering says yes. Here is the output from glxinfo | grep rendering:

direct rendering: Yes
X Error of failed request:  BadDrawable (invalid Pixmap or Window parameter)
  Major opcode of failed request:  137 (XFree86-DRI)
  Minor opcode of failed request:  9 ()
  Resource id in failed request:  0x4200004
  Serial number of failed request:  44
  Current serial number in output stream:  44


Many thanks if I could get some help

---

