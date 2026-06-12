---
title: "New Kernel and Wrong CPU Temp"
date: 2008-11-04
forum: General Help
---

### Post by darkcrawler on 2008-11-04
A few days ago i upgraded to Ubuntu 8.10 with 2.6.27-7 kernel, and the CPU temp shown with lm-sensors become wrong.
Usually with the last kernel 2.6.24-21 and 1/2% load of CPU, the temp was about 28°C.
Now with Kernel 2.6.27-7 and the same CPU load the temp is about 44°C.

I tried to boot with the old Kernel and temp is still 28°, windows XP temp tools (like coretemp) show that temp is 28/29°C, then i guess the right temp of my CPU is really 28/29°C.

I removed and reinstalled lm-sensors a few times but nothing change. "sensors" command still show me wrong cpu temp. Don't know what to do..Someone can help me? Thanks

---

### Post by darkcrawler on 2008-11-25
no one with the same problem?

---

### Post by darkcrawler on 2008-12-01
up..

---

### Post by Wayne_V on 2008-12-01
I didn't start seeing this until 2.6.27-9.  It seems most of the sensor limits (defined in /etc/sensors3.conf) are  wrong now:

```
# sensors
w83627thf-isa-0290
Adapter: ISA adapter
my VCore:    +1.38 V  (min =  +0.00 V, max =  +3.84 V)   
+12V:       +12.10 V  (min =  +3.34 V, max =  +3.47 V)   ALARM
+3.3V:       +3.25 V  (min =  +2.93 V, max =  +1.94 V)   ALARM
+5V:         +5.04 V  (min =  +2.43 V, max =  +6.27 V)   
-12V:        +5.73 V  (min = -11.04 V, max =  -9.32 V)   ALARM
V5SB:        +5.11 V  (min =  +3.84 V, max =  +0.54 V)   ALARM
VBat:        +3.20 V  (min =  +0.74 V, max =  +3.84 V)   
fan1:       1506 RPM  (min = 1424 RPM, div = 4)
CPU Fan:    2596 RPM  (min = 2235 RPM, div = 4)
fan3:          0 RPM  (min =   51 RPM, div = 128)  ALARM
M/B Temp:    +32.0°C  (high =  +9.0°C, hyst = -117.0°C)  ALARM  sensor = thermistor
CPU Temp:    +47.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = diode
temp3:       -48.0°C  (high = +80.0°C, hyst = +75.0°C)  sensor = thermistor
cpu0_vid:   +1.388 V
beep_enable:enabled
# dmesg | grep w836
[   18.694477] w83627hf: Found W83627THF chip at 0x290
[   18.694559] w83627hf w83627hf.656: Reading VID from GPIO5
```

I just stopped sensord for now --- haven't had a chance to look into this yet.

---

### Post by Wayne_V on 2009-01-26
Finally had some time to tweak this.   I modified sensors3.conf as follows:

```

chip "w83627thf-*" "w83637hf-*"

# Rather than an internal inverting op amp, the 627thf uses standard positive
# inputs and the negative voltages are level shifted by a 3.6V reference
# (same as 82d/83s).
# The math is convoluted, so we hope that your motherboard
# uses the recommended resistor values.
# Note that in1 (+12V) is the usual in4, and in4 (-12V) is the usual in5.
# Data sheet is obviously wrong for in4, the usual formula should work.
# No in5 nor in6.

    label in0 "VCore"
    label in1 "+12V"
    label in2 "+3.3V"
    label in3 "+5V"
    label in4 "-12V"
    label in7 "V5SB"
    label in8 "VBat"
# my BIOS does not display -12V so I ignored it
    ignore in4

# Mori Hiroyuki reported to need this (P4P800)
#    compute in0 @/2, @*2

    compute in1 ((28/10)+1)*@, @/((28/10)+1)
    compute in3 ((34/51)+1)*@, @/((34/51)+1)
    compute in4 -3.8*@, -@/3.8
    compute in7 ((6.8/10)+1)*@ ,  @/((6.8/10)+1)

# set limits to  5% for the critical voltages
# set limits to 10% for the non-critical voltages
# set limits to 20% for the battery voltage
# if your vid is wrong, you'll need to adjust in0_min and in0_max

   set in0_min cpu0_vid * 0.95
   set in0_max cpu0_vid * 1.05
   set in1_min 12 * 0.90
   set in1_max 12 * 1.10
   set in2_min 3.3 * 0.90
   set in2_max 3.3 * 1.10
   set in3_min 5.0 * 0.95
   set in3_max 5.0 * 1.05
   set in4_max -12 * 1.10
   set in4_min -12 * 0.90
   set in7_min 5 * 0.95
   set in7_max 5 * 1.05
   set in8_min 3.0 * 0.80
   set in8_max 3.0 * 1.20

# set up sensor types (thermistor is default)
# 1 = PII/Celeron Diode; 2 = 3904 transistor;
# 3435 = thermistor with Beta = 3435
# If temperature changes very little, try 1 or 2.
#   set temp1_type 1
#   set temp2_type 2
#   set temp3_type 3435

    label temp1 "M/B Temp"
    label temp2 "CPU Temp"
   label temp3 "Unknown Temp Sensor"
    ignore temp3

    set temp1_max        60
    set temp1_max_hyst    50
    set temp2_max        65
    set temp2_max_hyst    60

    label fan1 "Case Fan"
    label fan2 "CPU Fan"
    label fan3 "PS Fan"
    ignore fan3

    set fan2_div 4
    set fan1_min    1000
    set fan2_min    1000
    set fan3_min    1000

```

Now the values displayed by sensors seem to echo what the BIOS H/W Monitor page shows (and that's the only confirmation that any of my changes are any where near valid):

```

$ sudo sensors -s
$ sensors
w83627thf-isa-0290
Adapter: ISA adapter
VCore:       +1.41 V  (min =  +1.31 V, max =  +1.46 V)   
+12V:       +12.22 V  (min = +10.82 V, max = +13.19 V)   
+3.3V:       +3.15 V  (min =  +2.98 V, max =  +3.63 V)   
+5V:         +5.07 V  (min =  +4.75 V, max =  +5.25 V)   
V5SB:        +5.16 V  (min =  +4.76 V, max =  +5.24 V)   
VBat:        +3.17 V  (min =  +2.40 V, max =  +3.60 V)   
Case Fan:   1591 RPM  (min =  998 RPM, div = 8)
CPU Fan:    3096 RPM  (min = 1328 RPM, div = 4)
M/B Temp:    +38.0°C  (high = +60.0°C, hyst = +50.0°C)  sensor = thermistor
CPU Temp:    +47.5°C  (high = +65.0°C, hyst = +60.0°C)  sensor = diode
cpu0_vid:   +1.388 V
beep_enable:enabled

```

---

