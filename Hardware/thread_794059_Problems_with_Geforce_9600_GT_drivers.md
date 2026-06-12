---
title: "Problems with Geforce 9600 GT drivers"
date: 2008-05-14
forum: Hardware
---

### Post by wicke on 2008-05-14
I have download up-to-date driver (173.08 ) for my 9600 GT. After installation it works fine if I just start my GDM by "sudo /etc/init.d/gdm start" (stopped using "sudo /etc/init.d/gdm stop"). But when I reboot, I get an error message from GDM that informs about low screen resolution and asks for drivers.

Few files about this problem.

[My Xorg.0.log]("http://koti.mbnet.fi/wiili/xorg.log")
Found an error message:
"(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)"
[Xorg.conf file made by Nvidia installer]("http://koti.mbnet.fi/wiili/nvidia-xorg.conf")

I hope that someone can help.

---

