---
title: "Battery power management"
date: 2010-01-08
forum: Hardware
---

### Post by simhavcs on 2010-01-08
I am using ubuntu 8.04.

I have connected external battery , but 
$acpi -V command shows 80% charging, non-rechargable battery

Even if i remove the ac adapter and use the command

$acpi -V it shows ac adapter is connected and 80% charging.

From where does acpi picks the external battery information

Does acpi picks the battery information from Operating system level or Bios level?

Is there any method to pick the battery information from operating sytem level?

Even if i remove the battery connected to the system . BAT0 will be present in the /proc/acpi/battery/BAT0

Is there any way to add a new battery information?

---

