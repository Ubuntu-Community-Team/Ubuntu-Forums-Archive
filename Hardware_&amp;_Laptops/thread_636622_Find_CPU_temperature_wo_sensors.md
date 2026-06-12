---
title: "Find CPU temperature w/o sensors?"
date: 2007-12-10
forum: Hardware &amp; Laptops
---

### Post by vishzilla on 2007-12-10
Is it possible to find the CPU temperature w/o installing lm-sensors?

---

### Post by skug on 2007-12-10
I have found that ACPI reports the CPU temp as THERMAL_ZONE.

---

### Post by rockinlinux on 2007-12-10
how would you see it with acpi?

---

### Post by vishzilla on 2007-12-10
> **skug said:**
> I have found that ACPI reports the CPU temp as THERMAL_ZONE.

The ACPI THERMAL_ZONE folder is blank...so I guess ACPI doesnt report the CPU temperature. I think sensors will only detect the temperature in my computer.

---

### Post by vishzilla on 2007-12-10
> **rockinlinux said:**
> how would you see it with acpi?
a file will be present in /proc/acpi/* folder

---

