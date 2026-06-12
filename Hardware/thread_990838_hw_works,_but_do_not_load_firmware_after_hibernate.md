---
title: "hw works, but do not load firmware after hibernate"
date: 2008-11-23
forum: Hardware
---

### Post by johndouberro on 2008-11-23
I have got a dvb-usb stick, works good. System log after normal boot:

[INDENT][24839.096196] dvb-usb: found a 'Leadtek Winfast DTV Dongle (STK7700P based)' in cold state, will try to load a firmware 
[24839.096223] firmware: requesting dvb-usb-dib0700-1.10.fw 
[24839.281486] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw' 
[24839.497119] dib0700: firmware started successfully. 
[24840.000074] dvb-usb: found a 'Leadtek Winfast DTV Dongle (STK7700P based)' in warm state.[/INDENT]

But after hibernate, the system can't load firmware file:

[INDENT]dvb-usb: found a 'Leadtek Winfast DTV Dongle (STK7700P based)' in cold state, will try to load a firmware
[34722.990567] firmware: requesting dvb-usb-dib0700-1.10.fw
[34782.988059] dvb-usb: did not find the firmware file. (dvb-usb-dib0700-1.10.fw) Please see linux/Documentation/dvb/ for more details on firmware-problems. (-2)[/INDENT]

The dvb-usb works fine after unplugging and plugging.
Please, can someone tell me what is the problem? Maybe the solution could be to automatically disconnect and connect dvb-usb stick, if it is possible.

---

### Post by johndouberro on 2008-11-23
Forgot the details - configuration:
K/Ubuntu Intrepid, kernel 2.6.27-7-generic.

---

