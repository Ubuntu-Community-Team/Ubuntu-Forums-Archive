---
title: "help with 11.04 and RT2860 wireless chip"
date: 2011-06-27
forum: Hardware
---

### Post by jcspublic on 2011-06-27
First time Linux user/installer and I'm having trouble with wireless.

I have an AZIO card using a Ralink 2860 chip and I cannot get it to

1) see broadcasting wireless networks
2) connect to my own network using WPA2 (except in Ad-Hoc mode which doesn't provide me internet access)

When I run lshw -C Network I can see that the driver for my card is rt2800pci. When I try to replace this with a compiled rt2869sta driver (got latest from ralink's website) I no longer see wireless network options and lshw -C network shows no driver for my wlan0 device.

I've tried the 'backlist' technique where you blacklist all variants of rt2800 (presumably to make sure only rt2860 gets loaded) to no avail.

Any advice would be great.

This is allon a clearn install of 11.04 32-bit. I have wired internet access and have updated to the latest packages etc...

Thanks,
Josh

---

