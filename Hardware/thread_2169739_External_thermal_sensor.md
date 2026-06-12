---
title: "External thermal sensor"
date: 2013-08-23
forum: Hardware
---

### Post by 700 on 2013-08-23
Conditions:
- System: Ubuntu 12.04 / amd64
- Motherboard: ASUS crosshair V

Problem:
Wrong external thermal sensor readings whil BIOS readings are OK.
Temperature in my room is BELOW 30°C, but readings of all detected sensors by lm-sensors, Psensor (0.6.2.16) or HardInfo (0.5.1) most of the time look like below:
temp1 34.88°C
temp2 34.00°C
temp3 -128.00°C
temp1 34.88°C (MIN: 24; MAX: 66; lmsensor k10temp-pci-00c3)

How to get correct values? 
Correct values appear in BIOS only, so is it possible to get them directly from BIOS somehow?

---

### Post by tgalati4 on 2013-08-23
Where are the external sensors located?  What are the values in BIOS?  Those temperatures look normal if the sensors are inside the computer case.

---

### Post by 700 on 2013-08-23
> Where are the external sensors located?
External sensor is a loose cable (connected today to the OPT_TEMP1 connector) outside the computer case.

> What are the values in BIOS?
While checking BIOS it shows correct values (24°C) and when I touch it temperature jumps to over 35°C - but only on BIOS.
On lmsensor no values are changing according to the different conditions (touching).

---

### Post by tgalati4 on 2013-08-23
So that means that it is not detected and you are only reading CPU or motherboard sensors.  In a terminal, what is the output of:

```
sensors
```

What is the purpose of the external sensor?  Is there an alarm in the BIOS to trigger a shutdown if ambient temperature gets too high?  If that is the case, then test it out by wrapping with foil and heating with a match until shutdown is initiated.  Don't burn your house down.

---

### Post by 700 on 2013-08-23
Full output from the terminal:
> ~$ sensors
it8721-isa-0290
Adapter: ISA adapter
in0:          +2.81 V  (min =  +2.65 V, max =  +3.01 V)
in1:          +2.77 V  (min =  +3.04 V, max =  +2.00 V)  ALARM
in2:          +1.12 V  (min =  +1.67 V, max =  +2.14 V)  ALARM
+3.3V:        +3.31 V  (min =  +6.10 V, max =  +5.14 V)  ALARM
in4:          +2.70 V  (min =  +1.76 V, max =  +2.96 V)
in5:          +2.52 V  (min =  +2.99 V, max =  +2.29 V)  ALARM
in6:          +0.82 V  (min =  +3.01 V, max =  +3.06 V)  ALARM
3VSB:         +2.23 V  (min =  +0.74 V, max =  +2.76 V)
Vbat:         +3.41 V  
fan1:        3426 RPM  (min =   15 RPM)
fan2:           0 RPM  (min =   10 RPM)  ALARM
temp1:        +43.0°C  (low  = -60.0°C, high = -17.0°C)  ALARM  sensor = thermistor
temp2:        +33.0°C  (low  = -17.0°C, high = -17.0°C)  ALARM  sensor = thermistor
temp3:       -128.0°C  (low  = +45.0°C, high = -18.0°C)  sensor = disabled
intrusion0:  OK

fam15h_power-pci-00c4
Adapter: PCI adapter
power1:       43.01 W  (crit = 124.95 W)

k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +31.4°C  (high = +70.0°C)
                       (crit = +90.0°C, hyst = +87.0°C)


> What is the purpose of the external sensor?
Room temperature measurement, data and experience collection. Nothing wrong, nothing illegal :P

---

### Post by tgalati4 on 2013-08-23
So you have a power meter that shows up, but your external sensor does not show up.  You will have to do some more research on how to read it.  Perhaps an acpi call or upgrade the BIOS so that it exposes it to the OS.  You have two different temp1 sensors, but they are measuring different temperatures.  If you hold your fingers on the external sensor and run sensors again and you don't see any rise in temperature in either temp1 then it is not being detected by lm-sensors.

---

### Post by 700 on 2013-08-25
How to skip BIOS, acpi and lm-sensors (Python?)? 
How to make those values alive from scratch?

---

### Post by tgalati4 on 2013-08-25
The temperature is simply stored in a memory location.  If you know the memory location exactly, then you can read it.  If you have it installed on your system, read through the following:

```
sudo acpidump
acpitool -e
```

It might look something like:


tgalati4@tpad-Gloria7 ~ $ acpitool -e
  Kernel version : 2.6.28.10-slim   -    ACPI version : 20080926
  -----------------------------------------------------------
  Battery #1     : present
    Remaining capacity : 43080 mWh, 100.0%
    Design capacity    : 51830 mWh
    Last full capacity : 43080 mWh, 83.12% of design capacity
    Capacity loss      : 16.88%
    Present rate       : 0 mW
    Charging state     : charged
    Battery type       : rechargeable, LION
    Model number       : IBM-92P1091
    Serial number      :    89

  AC adapter     : on-line 
  Fan            : enabled
  Fan Speed      : 3256 RPM

  CPU type               : Intel(R) Pentium(R) M processor 2.13GHz 
  Min/Max frequency      : 800/2133 MHz
  Current frequency      : 800 MHz
  Frequency governor     : ondemand 
  Freq. scaling driver   : acpi-cpufreq 
  Cache size             : 2048 KB
  Bogomips               : 1596.28 
  Processor ID           : 0
  Bus mastering control  : yes
  Power management       : yes
  Throttling control     : yes
  Limit interface        : yes
  Active C-state         : C0
  C-states (incl. C0)    : 4
  Usage of state C1      : 9 (0.0 %)
  Usage of state C2      : 214199 (93.9 %)
  Usage of state C3      : 13877 (6.1 %)
  T-state count          : 8
  Active T-state         : T0


  Thermal zone 1 : ok, 50 C
  Trip points : 
  ------------- 
  critical (S5):           99 C
  passive:                 95 C: tc1=5 tc2=4 tsp=600 devices= CPU 


   Device	S-state	  Status   Sysfs node
  ---------------------------------------
  1. LID	  S3	*enabled   
  2. SLPB	  S3	*enabled   
  3. UART	  S3	 disabled  pnp:00:09
  4. EXP0	  S4	 disabled  pci:0000:00:1c.0
  5. EXP1	  S4	 disabled  
  6. EXP2	  S4	 disabled  pci:0000:00:1c.2
  7. EXP3	  S4	 disabled  
  8. PCI1	  S4	 disabled  pci:0000:00:1e.0
  9. USB0	  S3	 disabled  pci:0000:00:1d.0
  10. USB1	  S3	 disabled  pci:0000:00:1d.1
  11. USB3	  S3	 disabled  pci:0000:00:1d.3
  12. USB7	  S3	 disabled  pci:0000:00:1d.7
  13. AC9M	  S4	 disabled

-------------------------------

Place the temperature probe in a cup of ice water.  If you don't see any low temperature values (0 to 3C) then the temperature sensor is not exposed to ACPI either.

---

### Post by 700 on 2013-08-27
Unfortunately It's not showing anything useful as well:
> Kernel version : 3.2.0-52-generi   -    ACPI version : 20110623
  -----------------------------------------------------------
  Battery status : <not available>

  AC adapter     : <info not available or off-line> 
  Fan            : <not available>

[...]

  Thermal info   : <not available>

   Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. SBAZ      S4    *disabled  pci:0000:00:14.2
  2. PS2K      S3    *enabled   pnp:00:0a
  3. P0PC      S4    *disabled  pci:0000:00:14.4
  4. UHC1      S4    *enabled   pci:0000:00:12.0
  5. UHC2      S4    *enabled   pci:0000:00:12.2
  6. USB3      S4    *enabled   pci:0000:00:13.0
  7. UHC4      S4    *enabled   pci:0000:00:13.2
  8. USB5      S4    *enabled   pci:0000:00:16.0
  9. UHC6      S4    *enabled   pci:0000:00:16.2
  10. UHC7      S4    *enabled   pci:0000:00:14.5
  11. PE20      S4    *disabled  
  12. PE21      S4    *disabled  
  13. PE22      S4    *disabled  
  14. PE23      S4    *disabled  
  15. PC02      S4    *disabled  pci:0000:00:02.0
  16. PC04      S4    *disabled  pci:0000:00:04.0
  17. PC05      S4    *disabled  pci:0000:00:05.0
  18. PC06      S4    *disabled  pci:0000:00:06.0
  19. PC07      S4    *disabled  pci:0000:00:07.0
  20. PC09      S4    *disabled  pci:0000:00:09.0
  21. PC0A      S4    *disabled  
  22. PC0B      S4    *disabled  
  23. PC0C      S4    *disabled  
  24. PC0D      S4    *disabled  
  25. PWRB      S3    *enabled
Where is this data stored? 
How to access it?

---

### Post by tgalati4 on 2013-08-27
Send an email to Asus and ask for a linux module to read the external temperature sensor.  Post the reponse that you get from them.

---

### Post by 700 on 2013-08-30
> **tgalati4 said:**
> Send an email to Asus and ask for a linux module to read the external temperature sensor.  Post the reponse that you get from them.
For my question:
"[COLOR=#333333][FONT=Arial]Where could I get Linux 64bit module for your Formula V motherboard OPT_TEMP1 [/FONT][/COLOR][COLOR=#333333][FONT=Arial]connector to read the external temperature sensor, please?"[/FONT][/COLOR]
Their answer is:
> [COLOR=#333333][FONT=Arial]For your issue, I suggest ask the local retailer for help as we don't sell any accessories in Uk.[/FONT][/COLOR]
So my modified question right now is below.
How to access (or make visible) correct values from  my external thermal sensor by skipping:
- BIOS
- acpi
- lm-sensors
- ASUS [FONT=Verdana]Customer Service[/FONT]

---

### Post by tgalati4 on 2013-08-30
Well that reply put a smile on my face.  I like to start the day reading humorous stuff.

I would dig into [lm-sensors]("http://lm-sensors.org/") development and write your own module.

---

