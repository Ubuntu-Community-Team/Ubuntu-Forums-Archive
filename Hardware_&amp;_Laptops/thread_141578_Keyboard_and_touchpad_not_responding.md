---
title: "Keyboard and touchpad not responding"
date: 2006-03-08
forum: Hardware &amp; Laptops
---

### Post by lipatden on 2006-03-08
I've compiled my own kernel for a Fujitsu-Siemens Lifebook E8010, when I boot the new kernel the keyboard and touchpad both don't seem to respond. I've tried enabling raw SERIO access, as the existing config seems to require this, but no luck.

Even goingto single user mode or recovery I still cannot type anything.

An advice?

---

### Post by Heliix on 2006-03-08
do do you still have the kernel you used before?
compare their config settings (on my laptop, config-2.6.10-old and config-2.6.15-new, for example), most notably the sections Input Devices and also serial/paralel ports, or the usb.. 
are you able to get the output of dmesg? this will provide you information about your hardware.(should be run from some kernel that may be old but just works, if you have some)
if you are sure your kernel configuration is OK and you didn't forget anything & still have no response from the keyboard.. try checking the xorg.conf file

as for the touchpad: hm.. that's tricky.. if you search through the ubuntu forums there are some touchpad-configuration howtos but so far, none of these worked for me in 2.6.15 kernel: only in 2.6.12. 
but don't be lazy to read them&try them!

you may also need to apply a kernel patch for usb-synaptics.. or at least i needed one

---

