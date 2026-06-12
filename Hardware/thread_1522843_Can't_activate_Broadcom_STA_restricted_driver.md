---
title: "Can't activate Broadcom STA restricted driver"
date: 2010-07-02
forum: Hardware
---

### Post by landersohn on 2010-07-02
I just installed Lucid 64bit. It boots OK with the 2.6.32-23 kernel (the 2.6.32.2 kernel hangs with a blinking text cursor) so I am reasonably happy.
Problem is when I tried to Activate the restricted driver for my Broadcom STA wireless card, I get an error message that the file /sys/module/wl/drivers
could not be created. Trying a
sudo mkdir 
to create this directory also failed with "No such file or directory".
Anybody got any ideas?

I got the wireless to work with an older driver that I used on Karmic but I'd like to understand this problem

---

### Post by Bachstelze on 2010-07-02
Try [font=monospace]mkdir -p[/font] instead of just [font=monospace]mkdir[/font].

---

### Post by landersohn on 2010-07-03
The "-p" makes no difference.

I got the wireless to work by manually installing an older broadcom driver tat I used on Jaunty before Broadcom STA was supported by the distro.
I compiled wl.ko, copied wl.ko into a manually created directory 
/lib/modules/kernel/net/wireless/wl
and I also copied the *.o files into a manually created directory 
/lib/modules/linux_restricted_modules/2.6.32.23/wl
and subsequently running 
depmod 
modprobe wl
depmod -A

This installed the wl module and somehow ended up creating the /sys/module/wl directory with subdirectories. 

It still puzzles me that activating the driver that comes with lucid does not work and that I can not create these directories in /sys/module. In fact, I can not create any directory in /sys/module using sudo mkdir.

---

