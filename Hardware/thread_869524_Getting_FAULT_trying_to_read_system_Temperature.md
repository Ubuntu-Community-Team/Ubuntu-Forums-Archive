---
title: "Getting FAULT trying to read system Temperature"
date: 2008-07-24
forum: Hardware
---

### Post by kdt_denton on 2008-07-24
Guys, I am getting a FAULT when trying to read the system
temperature. My sig contains system config. Any ideas?

```

kdt@kdt-lnx0:/etc/init.d$ sensors
f71882fg-isa-0600
Adapter: ISA adapter
3.3V:        +3.36 V
Vcore:       +1.26 V  (max =  +2.04 V)   
Vdimm:       +2.21 V
Vchip:       +1.74 V
+5V:         +5.42 V
12V:        +11.50 V
5VSB:        +3.86 V
3VSB:        +3.36 V
Battery:     +3.28 V
CPU:        1411 RPM
System:        0 RPM  ALARM
Power:         0 RPM  ALARM
Aux:           0 RPM  ALARM
CPU:         +39.0°C  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
[COLOR="Red"]System:        FAULT  (high = +85.0°C, hyst = +81.0°C)  
                      (crit = +100.0°C, hyst = +96.0°C)  sensor = [/COLOR]transistor
```

here is /etc/sensors3.conf:
```

chip "f71882fg-*"

# Temperature
    label temp1       "CPU"
    label temp2       "System"
    ignore temp3

# Fans
    label fan1        "CPU"
    label fan2        "System"
    label fan3        "Power"
    label fan4        "Aux"

# Voltage
    label in0         "3.3V"
    label in1         "Vcore"
    label in2         "Vdimm"
    label in3         "Vchip"
    label in4         "+5V"
    label in5         "12V"
    label in6         "5VSB"
    label in7         "3VSB"
    label in8         "Battery"

# never change the in0, in7 and in8 compute, these are hardwired in the chip!
    compute in0       (@ * 2), (@ / 2)
    compute in2       (@ * 2), (@ / 2)
    compute in3       (@ * 2), (@ / 2)
    compute in4       (@ * 5.25), (@ / 5.25)
    compute in5       (@ * 12.83), (@ / 12.83)
    compute in6       (@ * 5.25), (@ / 5.25)
    compute in7       (@ * 2), (@ / 2)
    compute in8       (@ * 2), (@ / 2)

```

---

### Post by kdt_denton on 2008-07-27
Guys, I think I found the answer to this. I dug into the datasheet from Fintek, the manufacturer of the super i/o chip in this mobo:

[http://www.datasheet4u.com/html/F/7/1/F71882_Fintek.pdf.html]("http://www.datasheet4u.com/html/F/7/1/F71882_Fintek.pdf.html")

On the LAST PAGE I noticed that the D3 line is labeled (System). Hmmm. In /etc/sensors3.conf, that line is set to ignore, so I changed the lines from:

```

# Temperature
    label temp1       "CPU"
    label temp2       "System"
    ignore temp3

```

TO:

```

# Temperature
    label temp1       "CPU"
    ignore temp2       "T2"
    label temp3       "System"

```

And boom! We have liftoff! Apparently MSI does not hook that D2 line to anything. I am going to try to confirm this with MSI ...

---

