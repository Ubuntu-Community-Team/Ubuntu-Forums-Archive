---
title: "ISA Adapter temperature"
date: 2023-12-23
forum: Hardware
---

### Post by daniell59 on 2023-12-23
I would appreciate if somebody would explain to me the following.

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +54.0°C  (crit = +100.0°C)
Core 1:       +51.0°C  (crit = +100.0°C)

---

### Post by daniell59 on 2023-12-23
> **dltech said:**
> Where you found a PC with ISA? It is older then PCI. By the way there is a k-pop singer ISA.

This computer must be 17 years old. I only wish that it would die so that I could have an excuse to build a new one.

---

### Post by Yellow Pasque on 2023-12-23
You have a dual core CPU. One core is 51C and the other is 54C. What is confusing you?

> Where you found a PC with ISA?
The ISA bus is still being used on modern mobos/systems as the interface to the sensor (Super I/O) chip even if the slots and add-in cards are long gone.

---

### Post by daniell59 on 2023-12-23
> **Yellow Pasque said:**
> You have a dual core CPU. One core is 51C and the other is 54C. What is confusing you?


The ISA bus is still being used on modern mobos/systems as the interface to the sensor (Super I/O) chip even if the slots and add-in cards are long gone.

aniel@daniel-P5Q-PRO:~$ sensors
radeon-pci-0100
Adapter: PCI adapter
temp1:        +70.0°C  

atk0110-acpi-0
Adapter: ACPI interface
Vcore Voltage:        1.13 V  (min =  +0.80 V, max =  +1.60 V)
 +3.3 Voltage:        3.30 V  (min =  +2.97 V, max =  +3.63 V)
 +5 Voltage:          5.14 V  (min =  +4.50 V, max =  +5.50 V)
 +12 Voltage:        12.10 V  (min = +10.20 V, max = +13.80 V)
CPU FAN Speed:      1383 RPM  (min =  600 RPM, max = 7200 RPM)
CHASSIS1 FAN Speed: 1577 RPM  (min =  600 RPM, max = 7200 RPM)
CHASSIS2 FAN Speed:    0 RPM  (min =  600 RPM, max = 7200 RPM)
POWER FAN Speed:    1548 RPM  (min =  600 RPM, max = 7200 RPM)
CPU Temperature:     +44.0°C  (high = +60.0°C, crit = +95.0°C)
MB Temperature:      +37.0°C  (high = +45.0°C, crit = +95.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +53.0°C  (crit = +100.0°C)
Core 1:       +50.0°C  (crit = +100.0°C)

daniel@daniel-P5Q-PRO:~$ 

Above it is CPU temperature. I thought that was the temperature. Thanks for your reply. Please forgive me if this is an inane question.

---

### Post by Yellow Pasque on 2023-12-23
The core temps are internal ones. The "CPU temperature" is usually taken from the heatspreader/socket, so it's common for it to be lower.

---

### Post by daniell59 on 2023-12-24
> **Yellow Pasque said:**
> The core temps are internal ones. The "CPU temperature" is usually taken from the heatspreader/socket, so it's common for it to be lower.

Thanks for clearing it up for me.

---

