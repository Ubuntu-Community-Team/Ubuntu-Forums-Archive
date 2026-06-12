---
title: "is my vga conected?"
date: 2009-09-04
forum: Hardware
---

### Post by Jenkins1 on 2009-09-04
Is it possible to detect if the vga cable is pluged in on boot?

---

### Post by moonscapex on 2009-09-04
My computer beeps if there is no display, however it is different on some systems, depending on the BIOS.

---

### Post by Jenkins1 on 2009-09-05
I would like to detect it so that if the vga cable is used then one xor.conf is used and if not the other xorg.conf is used.

---

### Post by Fafler on 2009-09-05
You might be able to read out monitor information from the I2C bus on you graphics card. Try 

```
find /sys | grep i2c
```

and look for something relevant. Make 2 different xorg.conf and a script that symlinks to the right one, depending on which monitor is present.

---

### Post by Jenkins1 on 2009-09-05
I have tried

```
find /sys | grep i2c
```


the output i get is /sys/bus/i2c
/sys/bus/i2c/uevent
/sys/bus/i2c/devices
/sys/bus/i2c/drivers
/sys/bus/i2c/drivers/dummy
/sys/bus/i2c/drivers/dummy/uevent
/sys/bus/i2c/drivers/dummy/unbind
/sys/bus/i2c/drivers/dummy/bind
/sys/bus/i2c/drivers/da903x
/sys/bus/i2c/drivers/da903x/uevent
/sys/bus/i2c/drivers/da903x/unbind
/sys/bus/i2c/drivers/da903x/bind
/sys/bus/i2c/drivers_probe
/sys/bus/i2c/drivers_autoprobe
/sys/class/i2c-adapter

they output is the same if the vga is plugged in or not. Is there anything else that I can search for? 

> **Fafler said:**
>   Make 2 different xorg.conf and a script that symlinks to the right one, depending on which monitor is present.

This is what I was planing to do although I haven't worked out how so any help would be appreciated.

---

### Post by Jenkins1 on 2009-09-07
bump!

---

