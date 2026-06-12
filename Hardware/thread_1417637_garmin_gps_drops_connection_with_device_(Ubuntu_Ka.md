---
title: "garmin_gps drops connection with device (Ubuntu Karmic)"
date: 2010-02-27
forum: Hardware
---

### Post by sotomajor on 2010-02-27
Hey,
I'm going nuts with this problem, so any help will be highly appreciated.

The problem is: when I connect device (Garmin GpsMap 60CSX) it allows to make only one successful call and then connection seems to be broken. 
Here is what I do step by step:
```
sudo modprobe garmin_gps
```Then connect device. dmsg says:
```

[ 1410.417520] USB Serial support registered for Garmin GPS usb/tty
[ 1410.417547] usbcore: registered new interface driver garmin_gps
[ 1410.417550] garmin_gps: v0.33:garmin gps driver
[ 1418.160155] usb 5-2: new full speed USB device using uhci_hcd and address 4
[ 1418.306549] usb 5-2: configuration #1 chosen from 1 choice
[ 1418.309457] garmin_gps 5-2:1.0: Garmin GPS usb/tty converter detected
[ 1418.309595] usb 5-2: Garmin GPS usb/tty converter now attached to **ttyUSB0**

```Then I try to touch device with gpstrans twice. First attempt is successful, second one failed though:```

mkotsur@n-fox:~$ sudo gpstrans -p**/dev/ttyUSB0** -i
GPStrans (ASCII) - Version 0.41
Copyright (c) 2005 by Carsten Tschach (tschach@zedat.fu-berlin.de)
Linux/KKJ mods by     Janne Sinkkonen <janne@iki.fi> (1996)
Copyright (c) 2000 German Grid by Andreas Lange <andreas.lange@rhein-main.de>
Copyright (c) 1998,2000 Mayko-mXmap mods by Matthias Kattanek <mattes@ugraf.com>
Copyright (c) 2001 Development by Joao Seabra-CT2GNL <seabra@ci.AAC.uc.pt>
Copyright (c) 2005 Development by Jim Van Zandt <jrvz@comcast.removeme.net>
Warning: device with product ID 292 is unknown - assuming it's like a GPS II.
[COLOR=Navy]Connected GPS [/dev/ttyUSB0] is: Garmin GPSMap60CSX Software Version - V4.0[/COLOR]

mkotsur@n-fox:~$ sudo gpstrans -p/dev/ttyUSB0 -i
GPStrans (ASCII) - Version 0.41
Copyright (c) 2005 by Carsten Tschach (tschach@zedat.fu-berlin.de)
Linux/KKJ mods by     Janne Sinkkonen <janne@iki.fi> (1996)
Copyright (c) 2000 German Grid by Andreas Lange <andreas.lange@rhein-main.de>
Copyright (c) 1998,2000 Mayko-mXmap mods by Matthias Kattanek <mattes@ugraf.com>
Copyright (c) 2001 Development by Joao Seabra-CT2GNL <seabra@ci.AAC.uc.pt>
Copyright (c) 2005 Development by Jim Van Zandt <jrvz@comcast.removeme.net>
[COLOR=Red]ERROR:  The GPS receiver is not responding.[/COLOR]
```Both: dmesg and device's screen show no status changes.

Same behaviour in MapSource which running over wine: first attempt successful and connection fail then.

Kernel version:
```

mkotsur@n-fox:~$ uname -ra
Linux n-fox 2.6.31-19-generic-pae #56-Ubuntu SMP Thu Jan 28 02:29:51 UTC 2010 i686 GNU/Linux
```

---

