---
title: "No Sensors for AMD Phenom II (790FX/SB750) Mainboard in Jaunty 9.04"
date: 2009-06-26
forum: Hardware
---

### Post by PorcelainMouse on 2009-06-26
From what I can tell, lm-sensors has a working driver for the sensors on my mainboard.  But somehow, it's not included in the package distributed by Ubuntu.   (See here for more information and links: [https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/316257](https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/316257) .)  Does someone know more information about the status of support for mainboards based on AMD 790FX/SB750 chipsets?

I *think* this is why my system cannot find any sensors to report.  'sensors-detect' produces this output:

> sudo sensors-detect
...
AMD K10 thermal sensors...                                  Success!
    (driver `to-be-written')
...
#----cut here----
# Chip drivers
# no driver for AMD K10 thermal sensors yet
#----cut here----

---

### Post by VastOne on 2009-07-11
> **PorcelainMouse said:**
> From what I can tell, lm-sensors has a working driver for the sensors on my mainboard.  But somehow, it's not included in the package distributed by Ubuntu.   (See here for more information and links: [https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/316257](https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/316257) .)  Does someone know more information about the status of support for mainboards based on AMD 790FX/SB750 chipsets?

I *think* this is why my system cannot find any sensors to report.  'sensors-detect' produces this output:

> sudo sensors-detect
...
AMD K10 thermal sensors...                                  Success!
    (driver `to-be-written')
...
#----cut here----
# Chip drivers
# no driver for AMD K10 thermal sensors yet
#----cut here----

I am also looking for the solution to this

---

### Post by n3had on 2009-12-29
[https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/316257](https://bugs.launchpad.net/ubuntu/+source/lm-sensors/+bug/316257)

Seems like they might get this working on kernel 2.6.33 right now i am running the rc2 version of the same and its still not working with updated lm-sensors package v 3.1.1


Phoronix
> AMD Phenom Gets Linux Thermal Driver
Posted by Michael Larabel on July 18, 2008
While AMD's financial outlook has been bleak with it closing down 12% today, if you're a Linux user -- particularly one with a quad-core Phenom processor -- there is good news to report from the AMD camp.

The quad-core AMD Phenom processors were first introduced late last year, but its Linux support has been a rough ride. The AMD 790FX Motherboard Chipset had worked well with Linux using an older Athlon 64 X2 processor, but when it was paired with a Phenom and an older Linux kernel, we experienced all sorts of issues. Those issues though were worked out when switching to a newer kernel / distribution. However, what has been missing from the Linux support for over the past six months has been any thermal monitoring support.

LM_Sensors, the popular open-source project for monitoring all sorts of hardware sensors, has been without any support for reading the thermal diodes on the Phenom CPUs. However, thanks to work by an independent developer, Rudolf Marek, and an AMD engineer, Andreas Herrmann, (along with others) it's now possible to read your quad-core AMD CPU temperature.

They have constructed a new driver for the AMD "K10" support and is based upon the LM_Sensors driver for earlier AMD processors. There is, however, a few caveats to be aware of, which are described in the LM_Sensors mailing list message. It's also been proposed that the k8temp driver be renamed to amdtemp. In the mailing list message is also talks of possible enhancements for the AMD K8 support.

This Phenom thermal monitoring support for Linux has yet to be formally committed to LM_Sensors, but we'd expect it will appear in a new LM_Sensors 3 release in the near future.

---

### Post by pulpo69 on 2009-12-29
install this driver for k10 thermal sensors?

[http://khali.linux-fr.org/devel/misc/k10temp/](http://khali.linux-fr.org/devel/misc/k10temp/)

found on this page [http://lm-sensors.org/wiki/Devices](http://lm-sensors.org/wiki/Devices)

---

### Post by pulpo69 on 2009-12-29
how to install this driver?

---

