---
title: "Elantech Touchpad stopped working after upgrade to Xenial"
date: 2016-10-12
forum: Hardware
---

### Post by richardcrichardc on 2016-10-12
I have an Acer ES1-411-C1WD laptop that I recently upgraded from Trusty to Xenial. After the upgrade the Touchpad stopped working.

The touchpad fails on kernels: 4.4.0-42-generic, 4.4.0-22-generic and 4.5.1-040501-generic. If I boot off the old kernel (3.13.0-96-generic) from Trusty, the touchpad works again.

In /var/log/dmesg I can see that the touchpad has been detected:

[    3.142329] psmouse serio2: elantech: assuming hardware version 4 (with firmware version 0x4a5f0b)[    3.161874] psmouse serio2: elantech: Synaptics capabilities query result 0x00, 0x15, 0x0d.
[    3.180111]  sda: sda1 sda2 < sda5 >
[    3.186219] sd 0:0:0:0: [sda] Attached SCSI disk
[    3.221352] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio2/input/input10

However the device does not show up in /proc/bus/input/devices.

I have the idea (correct or not) that the device should show up in the sysfs but it does not:
richardc@towerhill:~$ ls /sys/devices/platform/i8042/
driver  driver_override  modalias  power  serio0  subsystem  uevent

serio0, which is the keyboard appears in the sysfs, but not serio2.

It seems like the device has disappeared between booting and XOrg starting.

Any suggestions on how to troubleshoot further?

---

### Post by richardcrichardc on 2016-10-14
Turns out Xenial does not write to /var/log/dmesg.log. I was looking at the log of the last boot before I upgraded. When I run `dmesg` I get a different log which suggests I add i8042.nopnp as a kernel parameter, and that fixes the problem. This was not needed on the earlier kernels, so maybe there has been a regression in the pnp code.

---

