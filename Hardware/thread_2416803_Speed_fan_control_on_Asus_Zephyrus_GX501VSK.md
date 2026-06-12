---
title: "Speed fan control on Asus Zephyrus GX501VSK"
date: 2019-04-15
forum: Hardware
---

### Post by RaiGal on 2019-04-15
As the title suggests I am trying to find a way to control the fan speed on my Asus Zephyrus GX501VSK. The latest BIOS update has made the fan control very aggressive whereas the fans will spin at 2500rpm as soon as they hit 35 degrees. As a result the fans are on most of the time. Unfortunately, the BIOS in this laptop doesnt offer any control over the thermal performance of the fans. So far it has been impossible to find an older version of the BIOS to roll back as the manufacturer has refused to provide me with an older BIOS.

I have installed psensors to monitor the temperature. When I type
sensors

I get the following output:
iwlwifi-virtual-0
Adapter: Virtual device
temp1: +33.0°C

acpitz-virtual-0
Adapter: Virtual device
temp1: +36.0°C (crit = +103.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Package id 0: +37.0°C (high = +100.0°C, crit = +100.0°C)
Core 0: +36.0°C (high = +100.0°C, crit = +100.0°C)
Core 1: +37.0°C (high = +100.0°C, crit = +100.0°C)
Core 2: +37.0°C (high = +100.0°C, crit = +100.0°C)
Core 3: +37.0°C (high = +100.0°C, crit = +100.0°C)

pch_skylake-virtual-0
Adapter: Virtual device
temp1: +37.0°C

I installed fancontrol but I am getting a There are no pwm-capable sensor modules installed message when I try sudo pwmconfig
I have also tried i8kutils but it doesnt seem to work.

---

### Post by RaiGal on 2019-04-21
Bump!

---

