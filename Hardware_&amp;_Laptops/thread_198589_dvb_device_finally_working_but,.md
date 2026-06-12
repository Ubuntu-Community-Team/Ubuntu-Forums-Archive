---
title: "dvb device finally working but,"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by graveson on 2006-06-17
I finally got my dvb device to work .at least dmesg shows to the modules have been inserted properly.however when scanning using the scan command i always get this error :

scanning Hotbird-13.0E
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
initial transponder 10853000 H 27500000 3
>>> tune to: 10853:h:0:27500
WARNING: >>> tuning failed!!!
>>> tune to: 10853:h:0:27500 (tuning failed)
WARNING: >>> tuning failed!!!
ERROR: initial tuning failed
dumping lists (0 services)
Done.

anyone got any ideas on what this could be

---

### Post by easyease on 2006-06-17
is it a usb device? if so what info does "lsusb" give you in a terminal? im having similar error feedback when scanning with my usb dvb-t device.......
its finding nothing but it is recognising my device as being there in a "warm" state.

---

