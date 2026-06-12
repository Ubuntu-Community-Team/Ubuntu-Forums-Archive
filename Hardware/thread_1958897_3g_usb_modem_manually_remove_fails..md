---
title: "3g usb modem manually remove fails."
date: 2012-04-15
forum: Hardware
---

### Post by deepclutch on 2012-04-15
I got a Huawei K4505 3G Modem and it works fine in Linux. but, after disconnecting from network manager, I cannot "safely remove" modem. 
if I run "sync && eject /dev/sdb" or "umount/pumount /dev/sdb" it also fails.

I need some info how to manually "safely" remove this device, since, ubuntu does not be  able to safely remove neither My Kindle e-reader or this modem. 

regards,
dc

---

### Post by deepclutch on 2012-04-15
I tried this and it unmounted:
[http://forums.debian.net/viewtopic.php?f=5&t=52627#p311645](http://forums.debian.net/viewtopic.php?f=5&t=52627#p311645)

and it removes the drive. I hope, ubuntu will fix this bug with usb devices which are not usb flash memory, but devices like 3g modem etc.

---

### Post by deepclutch on 2012-04-29
I am fed up with this issue. Is there any fix for this. I am confused about the process to unbind usb modem. can anyone help?

when I put this K4505 Huawei modem on Windows 7, it is detected as a usb modem as well as a data storage device and mounted as a partition(it has mobile manager software pops up).

Is there something I miss? I fear this modem will get damaged if I force remove the device every time(although I make sure usb modem icon disappear in "computer:" in nautilus file manager). 

I did type these commands after finding usb port used is "2-1":
as root(sudo su) :

```
sync&&sync&&sync 
```

```
echo "auto" > "/sys/bus/usb/devices/usb2/2-1/power/level"
```

```
echo "2-1:1.1" > "/sys/bus/usb/devices/2-1\:1.0/driver/unbind"
```

^^ I hope these 2 steps are enough? but, I try to remove the device attributes also before pulling usb modem out of the port.

```
echo "1" > "/sys/bus/usb/devices/usb2/2-1/remove" 
```

Can someone guide Me whether I am doing is the correct way?

---

