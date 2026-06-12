---
title: "bluetooth keyboard &amp; mouse not working after suspend"
date: 2009-10-08
forum: Hardware
---

### Post by tpapp on 2009-10-08
Hi,

I am using the latest karmic.  My problem is that after suspend, my bluetooth keyboard and mouse stop working (ie they don't generate input events).  But everything looks fine:
- the BT device is active, the bluetooth icon is there on the panel,
- the devices appear to be connected when I check in the bluetooth Preferences,
- disconnecting & reconnecting the devices doesn't help,
- neither does disabling and enabling the BT hardware,
- if I delete and re-pair the devices, they pair just fine, but still no events.

However, if I reboot the laptop, everything works just fine.

Please help me debug this, even a workaround script would be great.

Computer is a Dell Latitude E6400, with Dell bluetooth keyboard and mouse.  I have searched for bugs similar to this, but in the ones I find, the problem is that the bluetooth hub is not working after suspend, my problem is with the devices.

Hardware info:
$ lsusb 
Bus 005 Device 002: ID 0a5c:5800 Broadcom Corp. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 018: ID 413c:8156 Dell Computer Corp. 
Bus 003 Device 017: ID 413c:8158 Dell Computer Corp. 
Bus 003 Device 016: ID 413c:8157 Dell Computer Corp. 
Bus 003 Device 015: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 028: ID 413c:2106 Dell Computer Corp. 
Bus 002 Device 027: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 026: ID 056a:0065 Wacom Co., Ltd 
Bus 002 Device 024: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 023: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 002 Device 022: ID 0424:2514 Standard Microsystems Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0c45:63f1 Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by siemer on 2010-01-05
I’m also using Karmic. I only use a bluetooth mouse, but it also stops working after suspend. Sometimes it even stops working while actually using the mouse.

The symptoms are similar, the hardware is different.

Did you find a solution?

---

### Post by cenzorrll on 2010-01-05
not sure if this will help, but on several laptops (hp tx2000 series at least) you have to add i8042.reset to the grub options

it basically tells the computer to restart the input methods on wakeup, so it might help

just:
```
gksu gedit /etc/default/grub
```
and on the line that says:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
change it to:
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i8042.reset"
```

let me know if that works, i'm curious to know if it works with other inputs other than those found on laptops.

---

### Post by ShamoIdol on 2010-01-25
Fixed it with this:

```

root@x40:~# cat /etc/acpi/start.d/90-fix-kbd
#!/bin/bash

sleep 5
echo -n "i8042" > /sys/bus/platform/drivers/i8042/unbind
echo -n "i8042" > /sys/bus/platform/drivers/i8042/bind

sleep 1
# sensivity & filepath is reset everytime as well 
echo -n "255" >  /sys/bus/serio/devices/serio*/sensitivity
root@x40:~#


```

Got idea from
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/216927](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/216927)

---

### Post by liju.g.chacko on 2011-12-16
In Satellite L640 (AMD athlon II processor --ubuntu amd x64) problem is not coming after disabling multi-coring for CPU.

---

