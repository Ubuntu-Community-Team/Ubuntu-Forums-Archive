---
title: "Kernel uprade nvidia failed"
date: 2008-11-22
forum: Hardware
---

### Post by d4v1dv00 on 2008-11-22
Hi there,

I am running Ibex and had upgraded my kernel-generic to kernel-server by installing both:

- linux-kernel-xxxx-server
- linux-restricted-modules-xxxx-server

but after the first reboot, i can get the correct resolution so what i did was temporary run gdm using low resolution mode. once got into gdm, i open Restricted Hardware and found my nVidia restricted hardware was turned off. Turning it on was not enabled even prompted me with super login. check system update but nothing surface.

then i restart the system and this round i choose to reconfigure X from the menu rather than select login low res mode or troubleshooting. i uses the generic (default) configuration rather than create new or use backup configuration.

then now i am able to login to gdm with non low res mode but the restricted driver still not working. no 3D acceleration and video performance reduced drastically.

help needed here.

thanks

---

### Post by davidsrsb on 2008-11-22
Server kernel and Nvidia graphics is an unusual combination. I wonder if it has been deliberately prevented

---

### Post by sdennie on 2008-11-22
You may not be able to run the server kernel and nvidia graphics because the server kernel has various Xen things enabled and the nvidia driver is not pleased by this.  You *might* be able to install the nvidia drivers manually with some sort of force flag but, I actually don't know.  Why are you using the server kernel?  To get 4G of RAM on a 32-bit machine?  If so, you'll likely have to build your own kernel (or run 64-bit).

---

