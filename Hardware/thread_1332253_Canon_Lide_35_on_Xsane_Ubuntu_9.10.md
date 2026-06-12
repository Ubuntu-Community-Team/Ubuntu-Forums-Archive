---
title: "Canon Lide 35 on Xsane Ubuntu 9.10"
date: 2009-11-20
forum: Hardware
---

### Post by Hakimjo on 2009-11-20
Hello, I am trying to run a Canon Lide 35 from Xsane on Ubuntu 9.10.  The scanner is recognised, but the dialog complains about an invalid argument when attempting to preview or scan.

The debug command yields the following report:

[sanei_debug] Setting debug level of genesys to 255.
[genesys] SANE Genesys backend version 1.0 build 11 from sane-backends 1.0.20
[genesys] sane_init: authorize != null
[genesys] sane_init: little endian machine
[genesys] probe_genesys_devices: start
[genesys] attach: start: devp != NULL, may_wait = 0
[genesys] attach: trying to open device `libusb:002:005'
[genesys] attach: device `libusb:002:005' successfully opened
[genesys] attach: found Canon flatbed scanner LiDE 35/40/50 at libusb:002:005
[genesys] attach: exit
[genesys] probe_genesys_devices: exit
[genesys] sane_init: exit
[genesys] sane_get_devices: start: local_only = false
[genesys] probe_genesys_devices: start
[genesys] attach: start: devp != NULL, may_wait = 0
[genesys] attach: device `libusb:002:005' was already in device list
[genesys] probe_genesys_devices: exit
[genesys] sane_get_devices: exit
WARNING: Unhandled message: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
[genesys] sane_exit: start
[genesys] sane_exit: exit

Looking forward to implementing the solution you will suggest !

Thanks

Joachim

---

