---
title: "Need help taming an over protective CPU fan"
date: 2009-09-16
forum: Hardware
---

### Post by shlape on 2009-09-16
I have a Dell Vostro 1710 which I recently installed v9.04 onto. All went well except, in comparison to the last distro I used, the CPU fan spins up often at low temperatures.

I have installed lm-sensors. I ran sensor-detect. Running 'sensors' on the command line gives:

> coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +29.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +29.0°C  (high = +100.0°C, crit = +100.0°C)

The 'coretemp' module exists and has been modprobe'd in.

I considered altering the /etc/sensors.conf file but could not find any convincing help online or from the comments within said file.

Can anyone help??

---

