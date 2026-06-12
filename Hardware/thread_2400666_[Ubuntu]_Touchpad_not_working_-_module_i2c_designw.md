---
title: "[Ubuntu] Touchpad not working - module i2c_designware_core can't be loaded"
date: 2018-09-08
forum: Hardware
---

### Post by zenerves on 2018-09-08
Hello all

I own two same laptops, ACER R131T

Upon upgrade of my daughter's, touchpad stopped working. 

She's on 18.04 (4.15.0), and up-to-date Arch (4.18.6). I am on outdated 16.10 (4.8.0).

The difference I see between the two are in lsmod, where on mine I have two i2c_designware_(something) modules loaded and not on my daughter's

*remmod* these on my laptop kills the touchpad

*modprobe* them on my daughter's laptop doesn't load them (as I can see with* lsmod|grep i2c*)


I can find in my daughter's laptop one i2c_designware-pci.ko file, on my laptop there are three of them: 

 > /lib/modules/4.8.0-54-generic/kernel/drivers/i2c/busses/i2c-designware-core.ko
 /lib/modules/4.8.0-54-generic/kernel/drivers/i2c/busses/i2c-designware-pci.ko
 /lib/modules/4.8.0-54-generic/kernel/drivers/i2c/busses/i2c-designware-platform.ko



I did try the grub edit "*GRUB_CMDLINE_LINUX_DEFAULT="i8042.reset quiet splash"*" to no avail. removing and reinserting i2c_hid doesn't work either.

there is an error message at end of boot, says
> 
   i2c_hid i2c_ELAN0501:00 Failed to reset device 
   i2c_hid i2c_ELAN0501:00 Can't add hid device -61


Any idea ?

---

