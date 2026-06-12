---
title: "Battery meter / ACPI info wrong"
date: 2009-02-22
forum: Hardware
---

### Post by SonicSteve on 2009-02-22
Hi friends,

I have a compaq laptop F700 series. The battery is a 4400 mah. Yet as you can see below the battery info shows it as 6000 mah. Also the battery is a 47 Wh battery as listed on the battery itself yet the meter thinks it is a 75 Wh battery. It seems that it has the specs completely wrong. Does anyone know how to fix this?

Product: Primary
Status: Charged
Percentage charge: 100.0%
Vendor: Hewlett-Packard
Technology: Lithium ion
Serial number: 
Model: Primary
Capacity: 63% (Poor)
Current charge: 47.6 Wh
Last full charge: 47.6 Wh
Design charge: 75.0 Wh


steve@Compaq-laptop:~$ sudo cat /proc/acpi/battery/*/state
[sudo] password for steve: 
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      3808 mAh
present voltage:         12499 mV
steve@Compaq-laptop:~$ sudo cat /proc/acpi/battery/*/info
present:                 yes
design capacity:         6000 mAh
last full capacity:      3808 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 197 mAh
design capacity low:     119 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard
steve@Compaq-laptop:~$

---

### Post by the_felis_leo on 2009-08-25
idem on Pavillon dv9217ea (serie dv9200/dv9000)
with new battery of 4200mAh :

```
design capacity:         6000 mAh
last full capacity:      4256 mAh
``````
leo@felis-kingdom:/proc/acpi$ uname -a
Linux felis-kingdom 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
```


also "remaining capacity" not accuraly repported.
try "acpi_apic_instance=2", seems to correct this second problem.
No more test done, need confirmation...

---

