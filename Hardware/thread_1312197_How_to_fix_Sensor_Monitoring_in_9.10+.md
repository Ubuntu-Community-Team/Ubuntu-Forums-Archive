---
title: "How to fix Sensor Monitoring in 9.10+"
date: 2009-11-02
forum: Hardware
---

### Post by Ttech on 2009-11-02
If you upgraded or preformed a new install to 9.10 and were trying to use lm-sensors you may have noticed this message: 
> ACPI: I/O resource it87 [0x295-0x296] conflicts with ACPI region IP__ [0x295-0x296]
ACPI: Device needs an ACPI driver

Take a look at this article [http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31]("http://www.lm-sensors.org/wiki/FAQ/Chapter3#Mysensorshavestoppedworkinginkernel2.6.31")

While not recommended, you can enable monitoring again by adding "acpi_enforce_resources=lax" to the kernel command line in grub.

---

### Post by bapoumba on 2009-11-05
Moved to Hardware.

---

