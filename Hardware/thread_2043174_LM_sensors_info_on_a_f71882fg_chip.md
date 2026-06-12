---
title: "LM sensors info on a f71882fg chip"
date: 2012-08-16
forum: Hardware
---

### Post by kainalu on 2012-08-16
Aloha,

I have the f71882fg chip, and noticed that the voltages do not make sense. Is there a way to interpret them correctly?


sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:        +27.0°C  (crit = +6280.3°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +41.0°C  (high = +80.0°C, crit = +100.0°C)
Core 1:       +39.0°C  (high = +80.0°C, crit = +100.0°C)
Core 2:       +42.0°C  (high = +80.0°C, crit = +100.0°C)
Core 3:       +38.0°C  (high = +80.0°C, crit = +100.0°C)

f71882fg-isa-0290
Adapter: ISA adapter
+3.3V:        +3.31 V  
in1:          +0.64 V  (max =  +2.04 V)
in2:          +1.18 V  
in3:          +1.18 V  
in4:          +0.91 V  
in5:          +0.96 V  
in6:          +1.33 V  
3VSB:         +3.25 V  
Vbat:         +3.20 V  
fan1:         631 RPM
fan2:        1045 RPM
fan3:        1628 RPM
fan4:           0 RPM  ALARM
temp1:        +27.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp2:        +47.0°C  (high = +85.0°C, hyst = +81.0°C)
                       (crit = +100.0°C, hyst = +96.0°C)  sensor = transistor
temp3:        +32.0°C  (high = +70.0°C, hyst = +68.0°C)
                       (crit = +85.0°C, hyst = +83.0°C)  sensor = transistor

---

### Post by RayVad on 2012-09-06
Allmost the same chip here and would like to know the correct information/calculations as well.
Anyone who configured a conf in /etc/sensors.d/ for the f71889fg chip?

My MOBO: MSI P55-GD65

---

### Post by RayVad on 2012-09-06
Hi Kainalu,

This is what i did find for your chip:

/etc/sensors3.conf von Debian / lm-sensors 3.0.2
================================================

#
# sample configuration for the Fintek f71882fg for MSI X58 Pro (7522-040R,
# like seen in Hetzner's EQ6 servers). To load the driver module, append a
# single line (without the #) to /etc/modules:
# f71882fg
#
chip "f71882fg-*"

# never change the in0, in7 and in8 compute, these are hardwired in the chip!
  compute in0       (@ * 2), (@ / 2)
  compute in2       (@ * 2), (@ / 2)
  compute in3       (@ * 2), (@ / 2)
  compute in4       (@ * 5.25), (@ / 5.25)
  compute in5       (@ * 11), (@ / 11)
  compute in6       (@ * 5.25), (@ / 5.25)
  compute in7       (@ * 2), (@ / 2)
  compute in8       (@ * 2), (@ / 2)

# Temperature
  # cpu temp is about 35 deg celsius (linux, idle)
  label temp1       "CPU"
  set temp1_max 70
  set temp1_crit 80
  # the IOH runs rather hot, even with an idle system 60..65 deg celsius
  # are seen. DO NOT ACTIVATE CPU SMART FAN OR IT WILL GET EVEN HOTTER!
  label temp2       "IOH"
  set temp2_max 80
  set temp2_crit 90
  # system is about 40 deg celsius (linux, idle)
  label temp3       "System"
  set temp3_max 50
  set temp3_crit 55

# Fans
  # value (CPU smart fan disabled!) is about 2300 rpm (linux, idle)
  label fan1        "CPU"
  ignore fan2
  # value is about 2200 rpm (linux, idle)
  label fan3        "System2"
  ignore fan4

# Voltage
  label in0         "3.3V"
  label in1         "Vcore"
  # BIOS (loaded) in1 == 1.25V
  # linux idle in1 == 1.05V (?)
  set in1_max 1.35
  ignore in2
  ignore in3
  label in4         "+5V"
  label in5         "12V"
  ignore in6
  label in7         "3VSB"
  label in8         "Battery"

---

