---
title: "adjusting /etc/sensors3.conf for a dual processor machine"
date: 2011-09-23
forum: Hardware
---

### Post by graysky on 2011-09-23
I'd like to get my cores from the sensors output to be consistent, i.e. core0-core7 for a dual xeon motherboard.  Here is what the output looks like currently.  Anyone have experience with this?

```

$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +65.0°C  (high = +85.0°C, crit = +95.0°C)
Core 1:       +65.0°C  (high = +85.0°C, crit = +95.0°C)
Core 9:       +66.0°C  (high = +85.0°C, crit = +95.0°C)
Core 10:      +66.0°C  (high = +85.0°C, crit = +95.0°C)

coretemp-isa-0004
Adapter: ISA adapter
Core 0:       +54.0°C  (high = +85.0°C, crit = +95.0°C)
Core 1:       +56.0°C  (high = +85.0°C, crit = +95.0°C)
Core 9:       +60.0°C  (high = +85.0°C, crit = +95.0°C)
Core 10:      +61.0°C  (high = +85.0°C, crit = +95.0°C)

smsc47b397-isa-0480
Adapter: ISA adapter
fan1:        1730 RPM
fan2:        1746 RPM
fan3:        1224 RPM
fan4:        2825 RPM
temp1:        +46.0°C
temp2:        +37.0°C
temp3:        +23.0°C
temp4:       -128.0°C
```

EDIT: Here is the solution, 2 steps:

1) ID what each chip is reporting
2) Reassign it to what you want

**Step 1**
Run sensors with the -u switch to see what options are available:

```
$ sensors -u coretemp-isa-0000
coretemp-isa-0000
Adapter: ISA adapter
Core 0:
  temp2_input: 61.000
  temp2_max: 85.000
  temp2_crit: 95.000
  temp2_crit_alarm: 0.000
Core 1:
  temp3_input: 61.000
  temp3_max: 85.000
  temp3_crit: 95.000
  temp3_crit_alarm: 0.000
Core 9:
  temp11_input: 62.000
  temp11_max: 85.000
  temp11_crit: 95.000
Core 10:
  temp12_input: 63.000
  temp12_max: 85.000
  temp12_crit: 95.000

$ sensors -u coretemp-isa-0004
coretemp-isa-0004
Adapter: ISA adapter
Core 0:
  temp2_input: 53.000
  temp2_max: 85.000
  temp2_crit: 95.000
  temp2_crit_alarm: 0.000
Core 1:
  temp3_input: 54.000
  temp3_max: 85.000
  temp3_crit: 95.000
  temp3_crit_alarm: 0.000
Core 9:
  temp11_input: 59.000
  temp11_max: 85.000
  temp11_crit: 95.000
Core 10:
  temp12_input: 59.000
  temp12_max: 85.000
  temp12_crit: 95.000
```

**Step 2**
Create file /etc/sensors.d/cores.conf and put the following statements in it:

```
chip "coretemp-isa-0000"

    label temp2 "Core 0"
    label temp3 "Core 1"
    label temp11 "Core 2"
    label temp12 "Core 3"

chip "coretemp-isa-0004"

    label temp2 "Core 4"
    label temp3 "Core 5"
    label temp11 "Core 6"
    label temp12 "Core 7"
```

Now when I run sensors, I get consistent output!  I hope this helps someone else one day.

---

