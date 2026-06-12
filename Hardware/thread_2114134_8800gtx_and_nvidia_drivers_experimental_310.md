---
title: "8800gtx and nvidia drivers experimental 310"
date: 2013-02-09
forum: Hardware
---

### Post by th3g on 2013-02-09
Hi All!
I have a problem with my 8800gtx and nvidia drivers. 
I added the experimental 310 drivers from "Additional Drivers". (64 bit)
After reboot everything seems to work correctly, but after 1-2 minutes everything is going to stop on desktop, i can ONLY move my mouse pointer, nothing else ( i can't open dolphin, no ctr-alt-F1, no ctrl-al-can NOTHING)
I found a naive solutions: in the nvidia-setting panel, under the "PowerMizer" voice, switching from "Adaptive" to "Maximum Performance" setting,everthing work well.
Is there anybody in the forum that know how to fix this problem?
Ty all!

---

### Post by raihansergi on 2013-02-09
Experimental drivers are not recommended for common and usual activity. Im having a differ problem but its caused by same reason. Scheck for the recommended version. Otherwise if you cant do Anything right now, boot with the previous linux header with holding SHIFT when booting. You can delete the header manually from apt or Nautilus (filesystem):D ;)

---

### Post by th3g on 2013-02-09
Tnx for helping! :-)

So if i want everything work well i have to use some certified driver. i added the 310 exp. using additional drivers, if i want to use some certified drivers like:
[http://www.nvidia.it/object/linux-display-amd64-310.32-driver-it.html](http://www.nvidia.it/object/linux-display-amd64-310.32-driver-it.html)
i have to install it after exit xorg no? ( ctrl+alt+f1) and then i ha to type

sudo ./NVIDIA-Linux-x86_64-310.32.run

or i have to install something before install it ( headers, kernel source), or stop some service?

Tnx!

---

### Post by th3g on 2013-02-09
I've found this topic [https://forums.geforce.com/default/topic/505391/8800m-gts-linux-freeze/](https://forums.geforce.com/default/topic/505391/8800m-gts-linux-freeze/)
it seems that i can only install 173 drivers to avoid this problem, or modify the xorg entry for PowerMizer. 
Hope this help someone else :-)

---

