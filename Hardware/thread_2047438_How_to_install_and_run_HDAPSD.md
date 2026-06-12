---
title: "How to install and run HDAPSD"
date: 2012-08-24
forum: Hardware
---

### Post by MetalPotatoHead on 2012-08-24
I have a toshiba qosmio x770 with ubuntu 12.04 64 bit and when I run HDAPSD, the output is:

Sat Aug 25 03:20:31 2012: Starting hdapsd
Sat Aug 25 03:20:31 2012: WARNING: You did not supply any devices to protect, trying autodetection.
Sat Aug 25 03:20:31 2012: Adding autodetected device: sda
Sat Aug 25 03:20:31 2012: Could not find a suitable interface

in windows worked perfectly HDD protection

what can I do?

---

### Post by 2F4U on 2012-08-25
HDAPSD is just a daemon, and in order to properly work a kernel module hdaps is needed. Is the kernel module hdaps successfully loaded?

What does the command 

```
sudo modprobe -v hdaps
```

give?

---

### Post by MetalPotatoHead on 2012-08-25
insmod /lib/modules/3.2.0-29-generic/updates/dkms/thinkpad_ec.ko 
WARNING: Error inserting thinkpad_ec (/lib/modules/3.2.0-29-generic/updates/dkms/thinkpad_ec.ko): No such device
FATAL: Error inserting hdaps (/lib/modules/3.2.0-29-generic/updates/dkms/hdaps.ko): No such device

---

### Post by linrunner on 2012-08-25
Hi,

there is no way to run hdapsd on your hardware. hdapsd plus the necessary kernel modules from tp-smapi-dkms package work on ThinkPads only.

Nothing similar exists for other laptop brands on Linux.

---

