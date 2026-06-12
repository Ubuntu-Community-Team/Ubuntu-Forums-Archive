---
title: "Fan speed control based on Hard Drive temperature?"
date: 2008-06-08
forum: Hardware
---

### Post by nyvaerld on 2008-06-08
Hey everyone,
So I have installed lm-sensors and hddtemp, and I've run pwmconfig.  The problem is, pwmconfig can only bind fan speeds to sensors built onto the motherboard; I'd like to control the fan that is underneath my hard drives, but pwmconfig doesn't see the hard drive temperature sensors.
Does anyone know of a way to control fan speeds based on hard drive temperatures?

Many thanks!

---

### Post by woodcarver on 2008-06-08
Those fans are not software controlled, they just blow constantly. You could build a board to thermostatically control them and power it from the PC's power supply.
If the drives are separated by atleast 1 full bay, they should not have temp. issues.

---

