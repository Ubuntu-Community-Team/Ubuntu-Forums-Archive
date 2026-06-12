---
title: "ASUS P5W DH - suspend/hibernate and temperatures monitor"
date: 2007-08-16
forum: Hardware &amp; Laptops
---

### Post by tjansson on 2007-08-16
I have a computer with a Asus P5W DH Deluxe motherboard and I would like to make suspend my desktop computer from time to time. Has anybody made this work and how? 

Furthermore I would like to be enable to read the temperatures and fan speeds as well. I have been looking at [http://www.hentges.net/misc/howtos/p5wdh/p5w_sensors.shtml](http://www.hentges.net/misc/howtos/p5wdh/p5w_sensors.shtml) and I would have thought that I justed need to load the module 

```

root@bohr:/home/tjansson# modprobe w83627ehf
FATAL: Error inserting w83627ehf (/lib/modules/2.6.20-16-generic/kernel/drivers/hwmon/w83627ehf.ko): No such device

```

but this obviously fails. Have anybody made it work?

---

