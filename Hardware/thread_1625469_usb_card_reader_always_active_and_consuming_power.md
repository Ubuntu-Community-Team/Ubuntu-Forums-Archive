---
title: "usb card reader always active and consuming power"
date: 2010-11-19
forum: Hardware
---

### Post by Axx83 on 2010-11-19
Hi guys. On my new notebook, Acer Travelmate 8172t there is a card reader which is always active even on battery power and uses at least 0.5w of power, constantly.

USB Device 2-1.6 : USB2.0-CRW (Generic)

on powertop and

Bus 002 Device 003: ID 0bda:0138 Realtek Semiconductor Corp.

as per lsusb


I put all usb ports on autosuspend after 2 seconds with this command:

```
sudo echo auto /sys/bus/usb/devices/*/power/level
sudo echo 2 /sys/bus/usb/devices/*/power/autosuspend
```

and everything is put to sleep BUT that device.

The only way I found is to remove the usb_storage module

```
sudo modprobe -r usb_storage
```

but this removes every usb storage device capability to my computer.

What else can I do ???

---

### Post by Axx83 on 2011-01-06
I still have not solved this problem. Does somebody has the same issue?

---

### Post by t.rei on 2013-01-16
Just encountered this on 13.04 and on a zenbook. Would shurely like to save the 8 to 9 W this device alone consumes.

However removing the module did not change a thing for me.

---

