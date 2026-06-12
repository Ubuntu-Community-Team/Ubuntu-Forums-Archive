---
title: "MSI GF75 Thin 8RD and cooler management"
date: 2021-07-12
forum: Hardware
---

### Post by alexander-can on 2021-07-12
[COLOR=#333333][FONT=&quot]Good day.[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]Please help me set up fancontrol on my [/FONT][/COLOR][COLOR=#BC2A4D][FONT=&quot]MSI[/FONT][/COLOR][COLOR=#333333][FONT=&quot] [/FONT][/COLOR][COLOR=#BC2A4D][FONT=&quot]GF75[/FONT][/COLOR][COLOR=#333333][FONT=&quot] [/FONT][/COLOR][COLOR=#BC2A4D][FONT=&quot]Thin[/FONT][/COLOR][COLOR=#333333][FONT=&quot] [/FONT][/COLOR][COLOR=#BC2A4D][FONT=&quot]8RD[/FONT][/COLOR][COLOR=#333333][FONT=&quot] laptop.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]There is such a feeling that the program does not see the sensors, or cannot control them, so the computer becomes very hot, the temperature of the processor cores and the NVideo card is about 99-100 degrees Celsius.[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Here is the output of the programs:[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]sensors-detect[/FONT][/COLOR]

sudo sensors-detect
# sensors-detect version 3.6.0
# System: Micro-Star International Co., Ltd. [COLOR=#BC2A4D]GF75[/COLOR] [COLOR=#BC2A4D]Thin[/COLOR] [COLOR=#BC2A4D]8RD[/COLOR] [REV:1.0] (laptop)
# Board: Micro-Star International Co., Ltd. MS-17F1
# Kernel: 5.4.0-74-generic x86_64
# Processor: Intel(R) Core(TM) i7-8750H CPU @ 2.20GHz (6/158/10)

This program will help you determine which kernel modules you need
to load to use lm_sensors most effectively. It is generally safe
and recommended to accept the default answers to all questions,
unless you know what you're doing.

Some south bridges, CPUs or memory controllers contain embedded sensors.
Do you want to scan for them? This is totally safe. (YES/no): y
Module cpuid loaded successfully.
Silicon Integrated Systems SIS5595... No
VIA VT82C686 Integrated Sensors... No
VIA VT8231 Integrated Sensors... No
AMD K8 thermal sensors... No
AMD Family 10h thermal sensors... No
AMD Family 11h thermal sensors... No
AMD Family 12h and 14h thermal sensors... No
AMD Family 15h thermal sensors... No
AMD Family 16h thermal sensors... No
AMD Family 17h thermal sensors... No
AMD Family 15h power sensors... No
AMD Family 16h power sensors... No
Hygon Family 18h thermal sensors... No
Intel digital thermal sensor... Success!
(driver `coretemp')
Intel AMB FB-DIMM thermal sensor... No
Intel 5500/5520/X58 thermal sensor... No
VIA C7 thermal sensor... No
VIA Nano thermal sensor... No


[COLOR=#333333][FONT=&quot]sensors:[/FONT][/COLOR]

sensors
pch_cannonlake-virtual-0
Adapter: Virtual device
temp1: +57.0°C

BAT1-acpi-0
Adapter: ACPI interface
in0: 12.75 V
curr1: 0.00 A

iwlwifi_1-virtual-0
Adapter: Virtual device
temp1: +35.0°C

coretemp-isa-0000
Adapter: ISA adapter
Package id 0: +43.0°C (high = +100.0°C, crit = +100.0°C)
Core 0: +42.0°C (high = +100.0°C, crit = +100.0°C)
Core 1: +42.0°C (high = +100.0°C, crit = +100.0°C)
Core 2: +40.0°C (high = +100.0°C, crit = +100.0°C)
Core 3: +41.0°C (high = +100.0°C, crit = +100.0°C)
Core 4: +41.0°C (high = +100.0°C, crit = +100.0°C)
Core 5: +40.0°C (high = +100.0°C, crit = +100.0°C)

acpitz-acpi-0
Adapter: ACPI interface
temp1: +45.0°C (crit = +100.0°C)



[COLOR=#333333][FONT=&quot]pwmconfig:[/FONT][/COLOR]

# pwmconfig version 3.6.0
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed



[COLOR=#333333][FONT=&quot]You can see that the speed of coolers was not found.[/FONT][/COLOR]

[COLOR=#333333][FONT=&quot]Tell me how you can enable control of coolers in the system?[/FONT][/COLOR]
[COLOR=#333333][FONT=&quot]Everything works very well under Windows 10, it stands as the second system. But Linux is needed for work.[/FONT][/COLOR]

---

