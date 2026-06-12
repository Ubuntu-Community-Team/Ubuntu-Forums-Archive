---
title: "[SOLVED] Asus K8U-X audio,ethernet,sensors - How to"
date: 2007-03-05
forum: Hardware &amp; Laptops
---

### Post by postadelmaga on 2007-03-05
-- Be sure to have the follow module in your kernel configuration
-- i suggest to download the last kernel from kernel.org 
-- and compile it like described here: [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

-- Note : in a standar ubuntu kernel you have all the modules so go on ...

Needed modules:
# Audio
    snd_intel8x0
# Ethernet:
    uli526x
# Sensors:
    it87, i2c_ali1563, i2c_ali15x3, i2c_ali1535
*************************************

How to :

after checking for the module do that :

## Audio
```
 : $ sudo nano /etc/modprobe.d/alsa-base
```
copy inside that lines at the end of file :

options snd-intel8x0 index=0
options snd-intel8x0  buggy_semaphore=1

as described here [http://www.ubuntuforums.org/showthread.php?p=817147#post817147](http://www.ubuntuforums.org/showthread.php?p=817147#post817147)

# Ethernet 
just add the module ali526x in the kernel --- >> eth1 now visible but don't work on my edgy (kernel 2.6.20.1)

# Sensors
install lm-sensors
```

$ sudo apt-get install lm-sensors
```
-- You may also need to remove k8temp module from the kernel (is unuseless in may case and cause problem )

(just to unload the module k8temp temporany)```
 modprobe -r k8temp
```

--- add that to /etc/modprobe.d/blacklist to exclude k8temp to load at boot time :

blacklist k8temp

-- add to /etc/modules/ these lines:

# I2C adapter drivers
i2c-ali1563
i2c-isa
# I2C chip drivers
it87

after that reboot and try launch 
```
$ sensors
```
to see temp and voltage

---

