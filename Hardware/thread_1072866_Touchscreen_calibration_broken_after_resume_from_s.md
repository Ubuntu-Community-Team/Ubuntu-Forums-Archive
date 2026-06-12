---
title: "Touchscreen calibration broken after resume from suspend / hibernate"
date: 2009-02-17
forum: Hardware
---

### Post by tmahring on 2009-02-17
Hi

I have an asus eeepc 901 running ubuntu mobile with an egalax touchcontroler soldered internally to an usb port.

I use the standard usbtouchscreen module and the xserver evtouch input module. i calibrated it with the standard calibration software provided with ubuntu mobile.

Everything normally works fine, but my problem is that every time i resume the system from a suspend or hibernate the calibration of the touchscreen gets completely ignored.
The same happens when i unload and reload the usbtouchscreen module.

the only way to get it working again is to completely reboot the system or to rerun calibration and restart the x session.
as i rely heavily on suspend this basicly renders my touchscreen completely useless.

one thing i noticed is that when i cat /proc/bus/input/devices the id of the touchscreen changes.
After boot the section of the touchscreen says
S: Sysfs=/devices/..../input/input8
which changes to 
S: Sysfs=/devices/..../input/input10
after resume.
after each reasume or module reload the number increases.


has anyone experienced a simmilar problem or has any idea how to solve this ?

any help would be greatly appreciated.

---

### Post by tmahring on 2009-02-17
ok guys, managed to find a workaround myself.

if anyone runs into the same problem:

/usr/share/hal/fdi/policy/10oshandler/50-eGalax

holds the default values used by the driver if no calibration has been used. if these are replaced by the values aquired by calibration the driver is always calibrated correctly.

---

