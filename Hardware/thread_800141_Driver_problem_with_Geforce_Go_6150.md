---
title: "Driver problem with Geforce Go 6150"
date: 2008-05-19
forum: Hardware
---

### Post by sethleach on 2008-05-19
I'm running Hardy Heron in KDE with a Geforce Go 6150 and I just can't seem to get it to work.

I've installed nvidia-glx and linux-restricted-modules, but when I try to enable the driver with nvidia-xconfig, I get the following error:

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.

---

### Post by Ayuthia on 2008-05-19
> **sethleach said:**
> I'm running Hardy Heron in KDE with a Geforce Go 6150 and I just can't seem to get it to work.

I've installed nvidia-glx and linux-restricted-modules, but when I try to enable the driver with nvidia-xconfig, I get the following error:

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Configured Video Device" must have a Driver
                  line.
This card should be using nvidia-glx-new instead of nvidia-glx.

---

### Post by sethleach on 2008-05-19
I tried that, but the output came out the same.

Some more information:

There's no "Driver" section under "Device" in /etc/X11/xorg.conf as there should be.
Nothing, not even "nv".

When I add the line "nvidia" as the driver and log out, X crashes when I try to start it.

It says that it can't load kernel module.

---

### Post by teaker1s on 2008-05-19
use envy for the binary driver

---

### Post by sethleach on 2008-05-19
I just tried envy.
It's giving the same error messages.

I even reinstalled Ubuntu.
No better.

---

### Post by nicedude on 2008-05-20
Try getting the Linux driver package directly from Nvidias website and using that. You will need to read all the directions to implement it though but I did and my laptops 8400m is working just fine :-)

---

### Post by sethleach on 2008-05-20
I just installed debian and the driver works fine now. 
Hopefully the Ubuntu crew will get that bug fixed soon... 
Thanks anyway.

---

