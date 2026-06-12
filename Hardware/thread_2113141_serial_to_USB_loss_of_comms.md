---
title: "serial to USB loss of comms"
date: 2013-02-06
forum: Hardware
---

### Post by cormacG on 2013-02-06
Hi,

[LIST]
[*][B]Problem: No serial data is seen on PC from a serial device connected by serial-to-USB adapter on ttyUSB0

[/B]
[*]Ubuntu 12.10 Desktop (configuration worked for months on 12.04, failed after a power cut. I've since upgraded to 12.10 but issue did not resolve as part of the upgrade)
[*]Serial to USB converter (Prolific U-232 & MCT-232  also tried). HW tested with other machines/OS and working OK
[*]Several different serial devices tried. HW tested with other machines/OS and working OK
[*]Drivers _appear_ correctly installed; any application tried e.g. minicom or gtkterm all "see" ttyUSB0 and connect to it. Physically removing and reconnecting the serial to USB connector makes ttyUSB0 appear & disappear.
[*]No unusual messages in dmesg
[/LIST]
My working hypothesis is somehow something in software that connects ttyUSB0 to the actual lower level HW has become corrupted or disconnected. Unfortunately my knowledge of Ubuntu doesn't stretch that far - pointers on where to look or what to do very much appreciated.



There has been a suggestion to "un-install & re-install" the drivers. I'd appreciate specifics on how to do that for the serial to USB drivers; those installed came with the Ubuntu OS and I don't want to screw with system files without specific guidance.


Thanks
Cormac

---

### Post by cormacG on 2013-02-12
This issue remains open (unsolved) - any insights appreciated.

Thanks
Cormac

---

### Post by cormacG on 2013-03-09
Resolved. chmod 666 /dev/ttyUSB0 is your friend... In the course of the upgrade from 12.04 to 12.10 something went awry with permissions... Is it a bit odd no errors were being thrown?

---

