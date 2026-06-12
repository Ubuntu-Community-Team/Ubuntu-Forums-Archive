---
title: "Dell Inspiron 6000 - kubuntu and lm-sensors"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by kou on 2007-08-01
Hi and thanks in advance for reading this post
I bought a laptop Dell Inspiron 6000 with 1 gb ram and I've installed Kubuntu 7.04. After this I've installed lm-sensors, and ksensors then I run 
$ sudo sensors-detect
and I put YES to all options

but at the end the script say :

**Sorry, no sensors were detected**.
Either your sensors are not supported, or they are connected to an
I2C or SMBus adapter that is not supported. See doc/FAQ,
doc/lm_sensors-FAQ.html or [http://www.lm-sensors.org/wiki/FAQ](http://www.lm-sensors.org/wiki/FAQ)
(FAQ #4.24.3) for further information.
If you find out what chips are on your board, check
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices) for driver status.

This laptop don't have sensors?
where can I find a guide or tutorial for making this application work? in google I found other guides but don't say anything about sensors in this  laptop hardware.

thanks

sorry for mi English... but I speak Spanish ;)

---

### Post by jpeddicord on 2007-08-04
There is something wrong with the sensors in Dells in 7.04. The functionality is there, but it has trouble detecting them. Try installing some sort of "i8k" package (search Aptitude). ACPI sensors still work fine though.

Jacob

---

### Post by bsalt on 2007-08-06
I've got the same issue jacobmp92.

My sensors picked up beautifully before Feisty. I guess something broke. But with hddtemp and acpi, I still have my CPU temp and HDD temp - just no fan speeds.

---

