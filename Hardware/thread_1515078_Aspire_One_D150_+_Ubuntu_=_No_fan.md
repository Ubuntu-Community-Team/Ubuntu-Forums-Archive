---
title: "Aspire One D150 + Ubuntu = No fan"
date: 2010-06-21
forum: Hardware
---

### Post by underwhelmd on 2010-06-21
Acer Aspire One - 1Gb ram, 160Gb HDD, was XP version. D150  

When I first bought this used, it had virus and spyware issues. I am a long time Linux user so figured this would be the perfect gadget to load Ubuntu Netbook edition on.  I had 10.4 running in minutes.  Wait a sec, it's getting hot... no fan kicking in. Fan worked under XP. 

Dmesg says- acerhdf: Acer Aspire One Fan driver, v.0.5.16 acerhdf: unknown (unsupported) BIOS version Acer      /Aspire one      /V1.11, please report, aborting!  
I started with Bios 1.05, flashed it to 1.11 in hopes it would help. Nope.  There is another version 1.13 but not sure it's for my model... don't want to brick it without advice.  

Anyways, this is exactly the opposite of most Aspire One fan posts....usually the fan won't shut off. Mine is a known working fan that won't turn on.  Considering putting XP back on it and selling, then finding a different model that has a bios supported. I thought I better ask about this first before admitting defeat.  Thanks in advance for any advice.  

acerhdf homepage clearly says: no acer d150 and d250 support !!!

---

### Post by underwhelmd on 2010-07-01
bump

---

### Post by underwhelmd on 2010-07-01
still no solution here.
I've tried 10.4 NBR, 9.10 NBR, alternate 9.10-lpia and now back to 10.4  desktop.

Same results with all the above- AA1 d150 overheats because fan won't  speed up when needed.  I feel like I've done my homework and just found  dead ends.

I've got laptop-mode working. Fan is found on boot and says it's on-   DMESG-

```

ACPI: Fan [FAN] (on)
ACPI: SSDT 3f597c90 00239 (v02  PmRef  Cpu0Ist 00003000 INTL 20051117)
ACPI: SSDT 3f596e10 001C7 (v02  PmRef  Cpu0Cst 00003001 INTL 20051117)
Marking TSC unstable due to TSC halts in idle
Switching to clocksource hpet
processor LNXCPU:00: registered as cooling_device1
ACPI: SSDT 3f597f10 000D0 (v02  PmRef  Cpu1Ist 00003000 INTL 20051117)
ACPI: SSDT 3f595f10 00083 (v02  PmRef  Cpu1Cst 00003000 INTL 20051117)
processor LNXCPU:01: registered as cooling_device2
thermal LNXTHERM:01: registered as thermal_zone0
ACPI: Thermal Zone [THRM] (27 C)


```I installed lm-sensors.  I've got a nice readout in the panel  that shows cpu coretemp accurately.  but that thermal zone never changes  from 27c.

sensors-detect finds the one sensor in the unit.
pwmconfig says-  There are no pwm-capable sensor modules installed

The fan comes on when I turn the unit on.  You can hear it speed up and  then stop oon power up.  

How can I get this thing working??    Thanks for any insights.

---

