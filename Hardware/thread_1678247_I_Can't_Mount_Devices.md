---
title: "I Can't Mount Devices"
date: 2011-01-30
forum: Hardware
---

### Post by Sugi on 2011-01-30
My devices aren't auto-mounting. :S  They are not in the media folder either including such devices as ipod, android phone, Sana Fuze Mp3 Player, etc.

How can I fix this?

tail /var/log/messages
kernel: [498000.880113] usb 1-4: reset high speed USB device using ehci_hcd and address 36

lsusb
Bus 001 Device 036: ID 04e8:681d Samsung Electronics Co., Ltd Galaxy Portal/Spica Android Phone

If I do this, I won't be able to fix other devices, if this even works...
I do not have this file in this location:
/etc/udev/rules.d/95-SyncAndroidSDCard.rules
[http://ubuntuforums.org/showthread.php?p=10404121](http://ubuntuforums.org/showthread.php?p=10404121)

Ubuntu 10.10 x64
Android Phone
Sugi

---

