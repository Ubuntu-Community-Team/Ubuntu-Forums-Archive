---
title: "invalid module format when insmod fpit_drv.so"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by chadraytay on 2007-06-10
I have a gateway cx2618 tablet pc.

I apt-get source the xorg fpit driver. Installed the necessary tools for compiling, and patched the source with some files from the gateway fpit thread so that clicking and rotation would work.

After compiling the source and doing a make / make install, if I "modprobe fpit_drv" I get module not found.

If I "insmod fpit_drv.so" I get -1 invalid module format.

I'm using 7.04 dvd edition.

Help? Thanks!

---

### Post by chadraytay on 2007-06-11
I've found it says the thing for the official module if I just apt-get install the fpit driver and try to load it.

---

### Post by chadraytay on 2007-06-13
Alright, I figured it out. The only things that are broken are modprobe and insmod. Or maybe ubuntu just broke them. Tried loading other modules and they all did -1 invalid module format. So instead I just installed the startup scripts for my tablet with the serial port settings and xorg.conf and somehow ubuntu decided it could load the invalid module as long as it was at startup.

---

