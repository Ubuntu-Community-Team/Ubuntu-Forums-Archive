---
title: "Error Unable to detect External hard disk enclosure controller"
date: 2017-07-10
forum: Hardware
---

### Post by ubuserone on 2017-07-10
Receive an ORICO Toolfree USB 3.0 to SATA External Hard Disk Drive Enclosure orico 3588us3.


Tested with both OS ubuntu 14.04 and 16.04


-Not able to detect controller type
-Not able to detect SMART health
-Disconnect every 5 minuite


Tested with windows OS 


-Able to detect SMART with Crystaldisk info but not complete.
-Not able to detect controller type
-Disconnect every 5 minuite

Install Smartctl on 14.04 with same output and crash.
```
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-71-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org


=== START OF INFORMATION SECTION ===
Vendor:               TO Exter
Product:              nal USB 3.0
Revision:             0103
User Capacity:        2,000,398,934,016 bytes [2.00 TB]
Logical block size:   512 bytes
Logical block provisioning type unreported, LBPME=-1, LBPRZ=0
Logical Unit id:      0x3020150331000720
Serial number:       
Device type:          disk
Local Time is:        Sun Jul  2 17:46:44 2017 EDT
SMART support is:     Unavailable - device lacks SMART capability.


=== START OF READ SMART DATA SECTION ===


Error Counter logging not supported


No self-tests have been logged



```

```

lsusb
ID 0080:a001

```

Found through the search [http://whatdoineed2do.blogspot.my/2017/06/orico-usb30-enclosure.html](http://whatdoineed2do.blogspot.my/2017/06/orico-usb30-enclosure.html)
[COLOR=#000000][FONT=&amp]The working enclosure had an unknown vendor/product ID 0080:a0001 (even when looking at the June 2017 [/FONT][/COLOR][usb id list]("http://www.linux-usb.org/usb-ids.html")[COLOR=#000000][FONT=&amp])

Lack of knowledge , should I follow and blacklist the usb for the fix ?


-Edit added extra picture upload on windows.
[/FONT][/COLOR][ATTACH=CONFIG]275967[/ATTACH]
VID  0080  PID A001
No infomation on [http://www.linux-usb.org/usb-ids.html](http://www.linux-usb.org/usb-ids.html)

---

