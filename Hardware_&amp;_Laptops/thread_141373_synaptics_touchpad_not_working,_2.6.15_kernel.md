---
title: "synaptics touchpad not working, 2.6.15 kernel"
date: 2006-03-08
forum: Hardware &amp; Laptops
---

### Post by Heliix on 2006-03-08
hi,
the same problem: 2.6.15 kernel, the same diagnosis as described by xtacocorex in this thread
[http://ubuntuforums.org/showthread.php?t=85654](http://ubuntuforums.org/showthread.php?t=85654) 
or by firecat53 in
[http://ubuntuforums.org/showthread.php?t=114973](http://ubuntuforums.org/showthread.php?t=114973)

i followed the advices and added "evdev" into /etc/modules, reboot.. and.. nothing changed. 

as to my kernel configuration, PS/2 mouse is as a module in input devices section, usb-synaptics is also a module, in USB HID section. i applied the kernel patch for usb-synaptics+2.6.15 kernel
no problems before (2.6.10 kernel). running Ubuntu Breezy on HP Omnibook 6100.

well, i would appreciate any help, because i know neither WHAT is wrong nor HOW TO FIND OUT what is wrong.. 
thanks
Heliix:(

---

### Post by xtacocorex on 2006-03-08
I don't know if it's the kernel module, but my problem was that I was using a debug version of Xorg which didn't allow for loading of modules within the xserver. 

It should be easy to check what xorg you are running with a search through synaptic.

The only way I could fix it was to reinstall the OS. It somehow picked the non-debug version in the install process. I don't think I did the install any different than I did initially. I wasn't able to remove the package and install the correct one for some reason. If that works for you, it'd be better than a reinstall.

---

### Post by Heliix on 2006-03-08
i installed Ubuntu on my new hdd a week ago and don't feel like going through the procedure again
Xorg -version: 6.8.2, release date 9/2/2006
module "mouse" is loaded from within X without problems 
(accordings to Xorg.0.log)

my old 2.6.10 kernel (which was pre-compiled on the installation cd) has no problems with synaptics but it seemed to me too large, too slow, stuffed with things i'll never need so i decided to compile a new kernel

maybe something wrong with the synaptics module itself -maybe some missing link, maybe wrong application of the kernel patch.. how can i check the synaptics module is OK? may I have some use from the "old kernel"?

---

