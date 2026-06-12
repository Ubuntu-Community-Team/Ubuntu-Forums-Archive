---
title: "System 76 Pangolin panp9 / Clevo W24AEU Fan control"
date: 2012-11-30
forum: Hardware
---

### Post by yiu on 2012-11-30
System 76 Pangolin panp9 / Clevo W24AEU Fan control

I recently purchased a Pangolin panp9 with Intel Core i7-3630QM Processor and Intel HD Graphics 4000.

Everything run well but I have a problem with the fan: at the moment it works only in On/Off state (quite noisy at office when it start).

I would like to control the fan speed so I tried 2 options, fancontrol or thinkfan.

1) fancontrol is based on sensors, but it cannot detect the fan (already used sensors-detect, no results)

command “sensors” output:

acpitz-virtual-0
Adapter: Virtual device
temp1:        +74.0°C  (crit = +120.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Physical id 0:  +75.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:         +73.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:         +74.0°C  (high = +87.0°C, crit = +105.0°C)
Core 2:         +71.0°C  (high = +87.0°C, crit = +105.0°C)
Core 3:         +71.0°C  (high = +87.0°C, crit = +105.0°C)

2) thinkfan should work on ACPI but I cannot find the fan control file

# 2) Fan control file
# ===================
# Specifies the path of the PWM fan control file. If there's none, we try the
# thinkpad_acpi interface with /proc/acpi/ibm/fan.
# Syntax:
# fan FAN_PATH
# Example:
# fan /sys/class/hwmon/hwmon3/device/pwm1

In my case no ibm directory, no pwm1, but I have 2 files:

/sys/class/hwmon/hwmon1/power/control
or
/sys/class/hwmon/hwmon1/device/power/control

( the text inside the files say just "auto")

this is the output of the command “acpi -V”

Battery 0: Full, 100%
Battery 0: design capacity 4400 mAh, last full capacity 3812 mAh = 86%
Adapter 0: on-line
Thermal 0: ok, 72.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 120.0 degrees C
Cooling 0: LCD 0 of 7
Cooling 1: Processor 0 of 3
Cooling 2: Processor 0 of 3
Cooling 3: Processor 0 of 3
Cooling 4: Processor 0 of 3
Cooling 5: Processor 0 of 3
Cooling 6: Processor 0 of 3
Cooling 7: Processor 0 of 3
Cooling 8: Processor 0 of 3

///////////////////////////////////////////////////////

I contacted System76 support and this is a resume of the answers:

“Fan speed is actually ACPI controlled based on temperature. The trigger itself is temp and it's either off or on. We're using a board from the Clevo model W24AEU in that unit” (but they have no other informations about the board that I suppose is a Clevo product).

All suggestions are welcomed.

Thanks !

---

### Post by phxpx on 2013-08-28
I want to do a similar thing. My ssd is heating a lot and it has no sensor so I want to run fan periodically.

---

