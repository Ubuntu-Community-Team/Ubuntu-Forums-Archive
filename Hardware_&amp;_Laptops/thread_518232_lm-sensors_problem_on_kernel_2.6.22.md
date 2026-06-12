---
title: "lm-sensors problem on kernel 2.6.22"
date: 2007-08-05
forum: Hardware &amp; Laptops
---

### Post by crhumber on 2007-08-05
I just compiled kernel 2.6.22 in order to try and get lm-sensors working with the w83627ehf module.  It now loads the module when I issue "sudo modprobe w83627ehf" whereas with my old kernel I got the error everyone else has been getting.  Now I have a new problem.  When I run "sensors' I get this error:
w83627dhg-i2c-9191-290
 ERROR: Can't get adapter or algorithm?!?


What's going on?  Please help...the only reason I upgraded my kernel was to get lm-sensors working!? thanks

---

### Post by crhumber on 2007-08-06
anybody?

---

### Post by daff_ on 2007-08-08
Sorry, can't help you, but I've got the exact same problem. So I'll *bump*.

---

### Post by bennyj on 2007-08-08
> **crhumber said:**
> I just compiled kernel 2.6.22 in order to try and get lm-sensors working with the w83627ehf module.  It now loads the module when I issue "sudo modprobe w83627ehf" whereas with my old kernel I got the error everyone else has been getting.  Now I have a new problem.  When I run "sensors' I get this error:
w83627dhg-i2c-9191-290
 ERROR: Can't get adapter or algorithm?!?


What's going on?  Please help...the only reason I upgraded my kernel was to get lm-sensors working!? thanks

thats becuase if you got to /sys/bus/i2c/devices.....that folder is no longer there.I have the same problem execpt i can get the sesors to read out by typing "sudo sensors" I just cant seem to figure out where it is getting the info from so i can reload it back into my conky?Any suggestions?

---

### Post by Bachstelze on 2007-08-09
From [http://www.lm-sensors.org/wiki/Kernel2.6](http://www.lm-sensors.org/wiki/Kernel2.6)

> In kernel 2.6.22, the way the I2C adapters are presented in sysfs changed, and this affects libsensors. You will need lm_sensors version 2.10.3 or later. Alternatively, the kernel can be compiled with CONFIG_SYSFS_DEPRECATED=y, then older version of lm_sensors will work fine.

lm_sensors is working fine here on a 2.6.22.

---

### Post by crhumber on 2007-08-09
The folder /sys/bus/i2c/devices is present, but my lm-sensors version is 2.10.1 so I'll try an update. Thanks for the replies.

---

### Post by crhumber on 2007-08-09
Ok, I got it working after upgrading to the latest lm-sensors version.  Thanks for the help

---

