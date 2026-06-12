---
title: "Overclocking with NVClock"
date: 2008-01-10
forum: Hardware &amp; Laptops
---

### Post by Bascote on 2008-01-10
Hey guys, I hope im not sent to nvclock forums since not many people are active there..

My problem is I have nvclock, im new to linux commands and im reading that to unlock pixel pipelines I need to:


Exit X: /etc/init.d/gdm stop

Unload module: modprobe -r nvidia_driver_here

Anyone have experience using this program to overclock/unlock their nvidia card?

Everytime I overclock whether its using nvclock or just in the nvidia properties, the values reset after a restart.

---

### Post by kidders on 2008-01-12
Hi there,

Afaik none of the settings nvclock can alter are stored in hardware, so they will all revert after a reboot, by design. You might want to throw your configuration changes into a script, so you can re-apply them automatically at boot.

---

### Post by Bascote on 2008-01-12
Yup I can do it every time but I'd rather have a script, but we're having a big problem figuring it out in this thread:

[http://ubuntuforums.org/showthread.php?t=665080](http://ubuntuforums.org/showthread.php?t=665080)

---

