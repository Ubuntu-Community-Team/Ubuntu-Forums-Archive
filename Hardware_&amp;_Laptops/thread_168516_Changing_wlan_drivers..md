---
title: "Changing wlan drivers."
date: 2006-04-30
forum: Hardware &amp; Laptops
---

### Post by darkshadow on 2006-04-30
I just bought a Acer Travelmate 4404 and installed Ubuntu 6.06 every thing is working good but I am having a little trouble with the networking. I have over 6 years Linux experience but for some reason I never used modules much and would like to know the proper way to set this up as I would usually recompile a kernel to get rid of the wrong version and have no problems, but I want to leave the kernel untouched on this system.

Currently I have to do this to this command set to get networking

rmmod bcm43xx (it does not work well)
modprobe acer_acpi
echo "enabled : 1" > /proc/acpi/acer/wireless
modprobe ndiswrapper

What is the best way to do this in the init scripts so that I don't have problems when updates come available and so the networking is set up right when booting.

---

### Post by darkshadow on 2006-05-01
Ok after just randomly looking through files in the /etc directory I got part of this figured out.
So far I added acer_acpi and ndiswrapper to /etc/modules and I added  bcm43xx to /etc/modprobe.d/blacklist
The only problem is I tried adding "echo "Enabled : 1" > /proc/acpi/acer/wireless" to /etc/rc.local but after booting up I still have to manually type it then manually set the wlan settings.

All I need to figure out is where to put that command so it is done before the network settings are loaded from /etc/network/interfaces so that I have to do no manual settings.

---

