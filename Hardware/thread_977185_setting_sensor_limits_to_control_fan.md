---
title: "setting sensor limits to control fan?"
date: 2008-11-10
forum: Hardware
---

### Post by the666pack on 2008-11-10
hello,

i run intrepid ibex on an acer aspire 1692 and i recognized a message

"setting sensor limits"

during boot up.i wonder if i can change the sensor limits of my fan during this service.. making it start at a higher CPU temperature.

maybe someone has an idea?

thanks a lot,

greetings,

mario

---

### Post by the666pack on 2008-11-14
hello,

i want to provide some additional information... the command

# sensors-detect

does not detect any sensors on my system:

Sorry, no sensors were detected.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See
[http://www.lm-sensors.org/wiki/FAQ/Chapter3](http://www.lm-sensors.org/wiki/FAQ/Chapter3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.

HOWEVER the

# sensors

command shows some information about the current temperature of my
cpu, so at least SOME sensor actually is receiving the temperature:

acpitz-virtual-0
Adapter: Virtual device
temp1: +47.0°C (crit = +97.0°C)

now i tried to follow some proposed solution to alter this settings
but i dont even find the "acpitz-virtual-0" entry in the
/etc/sensors.conf file.

has anyone some idea how to adjust some kind of "fan-on" value for
this "virtual device"? would be nice to set it to 50°C instead of 40°C
as it is now.

thanks for any help and

greetings,

mario

---

