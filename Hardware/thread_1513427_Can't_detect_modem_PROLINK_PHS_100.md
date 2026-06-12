---
title: "Can't detect modem PROLINK PHS 100"
date: 2010-06-19
forum: Hardware
---

### Post by ragonz on 2010-06-19
I've read so many posts discussing 'bout how to install prolink modem. I've followed all the posts instructions, but still none of them could help me to detect this modem.

I've done all the steps explained in this link
```
http://nmlaxaman.blogspot.com/2009/04/prolink-phs100-hsdpa-workout-for-debian.html

```
in which many people succeded by following those steps. i already installed the latest usb_modeswitch, wvdial, gnome-ppp and all the things explained on that link.

First of all, i do all the steps explained on that nmxlaxaman link n then i restart my laptop. After then, without modem being plugged, i check with lsusb command n return 

Bus 007 Device 001: ID 0000:0000
Bus 006 Device 002: ID 046d:c052 Logitech, Inc.
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 004: ID 0000:0000
Bus 004 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000

Then, i plug the modem n check again with lsusb command, n it returned

Bus 007 Device 001: ID 0000:0000
Bus 006 Device 002: ID 046d:c052 Logitech, Inc.
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 004 Device 004: ID 1e0e:f000
Bus 004 Device 003: ID 04f2:b016 Chicony Electronics Co., Ltd
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000

there's a change in line 7, which means new device in usb port is detected. But after that, i check with wvdialconf command it says that no modem is detected. I try to check in network manager, but nothing deffrent. i dnt know what to do, some post said try to shut down the PC in 2 mins, n the modem will be detected. But not work on me. I just wonder that this modem is detected as new device in usb port but not being dtected as modem. Any suggestion?

Regards
Ragonz

---

