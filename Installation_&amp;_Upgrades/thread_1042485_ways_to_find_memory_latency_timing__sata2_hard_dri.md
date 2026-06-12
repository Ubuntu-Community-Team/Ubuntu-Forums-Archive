---
title: "ways to find memory latency timing / sata2 hard drive"
date: 2009-01-17
forum: Installation &amp; Upgrades
---

### Post by IQRules on 2009-01-17
Is there a Linux way to retrieve this information?

Something like,
CPU-Z is a freeware that gathers information on some of the main devices of your system. 


SATA 150 or SATA 2 (300) hard drive 
Cas Latency
Timing

---

### Post by mulp on 2009-02-01
> **IQRules said:**
> Is there a Linux way to retrieve this information?

Something like,
CPU-Z is a freeware that gathers information on some of the main devices of your system. 


SATA 150 or SATA 2 (300) hard drive 
Cas Latency
Timing

cas latency, timing and other memory-stuff install the package i2c-tools and run:

sudo modprobe eeprom
decode-dimms

for other hardware stuff install and run lshw-gtk

---

