---
title: "reset acpi for new battery?"
date: 2008-12-17
forum: Hardware
---

### Post by cl0ckwork on 2008-12-17
i just got a new battery for my HP pavillion dv9000 series laptop because the old one was shot.
when i put the battery in, power manager/acpi still gives me info from the old battery.
```
$ cat /proc/acpi/battery/BAT0/info
present:                 yes
design capacity:         6000 mAh
last full capacity:      3936 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 202 mAh
design capacity low:     122 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard

```

still displays that the battery is from HP even though its another manufacturer and it shows only 65% capacity even though i just took it out of the box two days ago.
any ideas what i need to do?

---

### Post by the_felis_leo on 2009-08-25
idem :

[LIST]
[*]no model number (appart "Primary"
[*]no serial number
[*]no build date
[*]bad design voltage (displayed : 6000mAh, real indicated on battery : 4200mAh)
[/LIST]
for info :

```
leo@felis-kingdom:/proc/acpi$ cat  battery/BAT0/info
present:                 yes
design capacity:         6000 mAh
last full capacity:      4256 mAh
battery technology:      rechargeable
design voltage:          14800 mV
design capacity warning: 217 mAh
design capacity low:     131 mAh
capacity granularity 1:  10 mAh
capacity granularity 2:  25 mAh
model number:            Primary
serial number:            
battery type:            LION
OEM info:                Hewlett-Packard

``````
leo@felis-kingdom:/proc/acpi$ cat  battery/BAT0/state 
present:                 yes
capacity state:          ok
charging state:          charged
present rate:            unknown
remaining capacity:      4256 mAh
present voltage:         16670 mV

``````
leo@felis-kingdom:/proc/acpi$ uname -a
Linux felis-kingdom 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux
```the battery is new and charged.
laptop model number: Pavillon dv9217ea (serie dv9200/dv9000)


another problem : it seems that the remaining capacity is not accurancy updated.
I've add kernel option : acpi_apic_instance=2   and now remaining capacity seems to be updated.
Strange; Need confirmation...

---

