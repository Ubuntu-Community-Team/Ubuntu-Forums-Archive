---
title: "udev rules do not make the proper changes"
date: 2013-03-26
forum: Hardware
---

### Post by randomlogic78 on 2013-03-26
Hello,

I am running xubuntu (I've tried the changes on both 32 and 64 bit variants) 12.04, all current updates have been applied.

I have the following udev rule in /etc/udev/rules.d/79-ftdi.rules

SUBSYSTEM=="usb", ATTRS{idVendor}=="2341", ATTRS{idProduct}=="0001", SYMLINK+="sensors/ftdi_%s{serial}", OWNER="sensor", GROUP="dialout", MODE="0660"

The symlink is created, and the group is changed to dialout, however, the owner does not change to sensor (the owner stays root, and the sensor user exists and I've logged into it) and the MODE stays 660 no matter what I put in the udev rule.

---

### Post by steeldriver on 2013-03-26
I'm not sure about this, but you could try 

```
OWNER[COLOR=#ff0000]:=[/COLOR]"sensor", GROUP[COLOR=#ff0000]:=[/COLOR]"dialout", MODE[COLOR=#ff0000]:=[/COLOR]"0660"
```

The := syntax supposedly 'locks' the assignment so that a later rule can't revert it - I used this form for a pluggable fingerprint reader and it seemed to work

---

### Post by randomlogic78 on 2013-03-26
It turns out the actual device file in the /dev/bus/... directory is changing correctly.  The /dev/ttyACM0 isn't changing owner though.  I added RUN+="/usr/bin/sudo /bin/sh -c 'chown sensor /dev/ttyACM0'" but this command does not seem to be running.  Or if it is running, has no effect.

---

### Post by randomlogic78 on 2013-03-26
The := did not change the problem.  The directory in /dev/bus/usb/003/### has the correct owner and group, but the device file /dev/ttyACM0 does not have the correct owner nor permissions

---

