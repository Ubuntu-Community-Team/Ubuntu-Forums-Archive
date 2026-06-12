---
title: "from onboard ati to nvidia"
date: 2008-06-30
forum: Hardware
---

### Post by supersonicdarky on 2008-06-30
How can I make the nvidia card (5500) work with ubuntu when there is an onboard ati? (this is at a friend's btw, and no direct access atm) The onboard card works fine, worked since ubuntu was installed but the nvidia one does not. Installing nvidia-glx or using the drivers from the nvida site doesn't work. The ati works fine until you install the nvidia-glx, which causes it to go into lowres mode. The nvidia card never has any output. It works fine under windows. How would I go about making the nvida work as the onboard is not suited for gaming.

[Here](http://pastebin.com/m58f13592) is the output of lshw (before installing drivers from nvidia site).

Any help?

---

### Post by Mikecore on 2008-06-30
> **supersonicdarky said:**
> How can I make the nvidia card (5500) work with ubuntu when there is an onboard ati? (this is at a friend's btw, and no direct access atm) The onboard card works fine, worked since ubuntu was installed but the nvidia one does not. Installing nvidia-glx or using the drivers from the nvida site doesn't work. The ati works fine until you install the nvidia-glx, which causes it to go into lowres mode. The nvidia card never has any output. It works fine under windows. How would I go about making the nvida work as the onboard is not suited for gaming.

[Here](http://pastebin.com/m58f13592) is the output of lshw (before installing drivers from nvidia site).

Any help?

disable the ATI onboard card in the BIOS setup. It will then look for your addon card ( nvidia ). also make sure you uninstall the ati drivers and reconfigure your /etc/X11/xorg.conf file

---

