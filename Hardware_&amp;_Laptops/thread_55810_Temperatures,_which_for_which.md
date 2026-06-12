---
title: "Temperatures, which for which?"
date: 2005-08-10
forum: Hardware &amp; Laptops
---

### Post by srijith on 2005-08-10
On by HP Ubuntu install on nc6120, I have three directories under /proc/acpi/thermal_zone - TZ1, TZ2 and TZ3. I am not sure which hardwares each represents. Any helps?

The contents of some of the files in each dir are as follows:
```

TZ1file: temprature
temperature 40 C

```

```

TZ1file: trip_points
critical (S5):           102 C
passive:                 100 C: tc1=1 tc2=2 tsp=100 devices=0xdf7ce4c0 
active[0]:               80 C: devices=0xc1464220 
active[1]:               65 C: devices=0xc1464140 
active[2]:               55 C: devices=0xc1464fa0 
active[3]:               40 C: devices=0xc1464f20 

```

```

TZ2 file: temprature
temperature 42 C

```

```

TZ2 file: trip_points
critical (S5):           103 C

```

```

TZ3 file: temprature
temperature 28 C

```

```

TZ3 file: trip_points
critical (S5):           102 C
passive:                 60 C: tc1=1 tc2=2 tsp=300 devices=0xdf7ce4c0 


```

---

### Post by gmc on 2005-08-10
[QUOTE=srijith]On by HP Ubuntu install on nc6120, I have three directories under /proc/acpi/thermal_zone - TZ1, TZ2 and TZ3. I am not sure which hardwares each represents. Any helps?

The contents of some of the files in each dir are as follows:
```

TZ1file: temprature
temperature 40 C

```

```

TZ1file: trip_points
critical (S5):           102 C
passive:                 100 C: tc1=1 tc2=2 tsp=100 devices=0xdf7ce4c0 
active[0]:               80 C: devices=0xc1464220 
active[1]:               65 C: devices=0xc1464140 
active[2]:               55 C: devices=0xc1464fa0 
active[3]:               40 C: devices=0xc1464f20 

```
[/QUOTE]

As a guess, I would say it's TZ1. To test it, search google for information on the trip_points file and how to set it. Then set your critical temprature to a lower value than 102C, say 40C. If this is the correct one, ubuntu should automatically shut the system down, thinking that the CPU temp is too hot. It's a kludge test but it will confirm these are the correct files.

G.

---

