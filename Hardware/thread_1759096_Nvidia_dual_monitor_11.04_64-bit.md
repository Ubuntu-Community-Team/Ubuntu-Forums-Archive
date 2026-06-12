---
title: "Nvidia dual monitor 11.04 64-bit"
date: 2011-05-15
forum: Hardware
---

### Post by saegeoff on 2011-05-15
Hello all.  I am having trouble getting my dual monitors to work in Ubuntu 11.04 64-bit.  I am able to get the NVidia drivers to install properly and everything seems to work as expected.  However, when I go into the NVIDIA X Server Settings dialog and switch my second monitor to TwinView things get a little weird.  My second monitor turns on and displays properly but the NVIDIA X Server application starts to act choppy. Sometimes it makes the system unresponsive, I have to do a hard poweroff (even though I can still move my mouse cursor).  Sometimes everything works to the point I go to save the X Config File but I have not been able to get past this point. I am thinking I may have to just manually edit the .conf file myself but I was wondering if anyone else experienced these problems?  If so, what is the work around?

---

### Post by saegeoff on 2011-05-15
I was able to get this to work but I had to manually create the xorg.conf file.  If anyone else is having this issue, another possible workaround is to make all your changes to get the dual screen to work but don't press the 'Apply' button.  Save the conf file (make a backup first) and then reboot.

---

