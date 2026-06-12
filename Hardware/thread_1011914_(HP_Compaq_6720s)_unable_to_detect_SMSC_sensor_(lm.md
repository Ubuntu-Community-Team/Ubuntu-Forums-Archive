---
title: "(HP Compaq 6720s) unable to detect SMSC sensor (lm-sensors); switching thermal-zones"
date: 2008-12-15
forum: Hardware
---

### Post by map84 on 2008-12-15
Hello,

I encountered following problem on my new HP Compaq 6720s on which I installed Ubuntu 8.10.

lm-sensors (sensors-detect) failed to correctly detect the fan's	

```
Do you want to scan for Super I/O sensors? (YES/no): yes
Probing for Super-I/O at 0x2e/0x2f
Trying family `National Semiconductor'...               	No
Trying family `SMSC'...                                 	Yes
Found unknown chip with ID 0x3600
Probing for Super-I/O at 0x4e/0x4f
Trying family `National Semiconductor'...               	No
Trying family `SMSC'...                                 	No
Trying family `VIA/Winbond/Fintek'...                   	No
Trying family `ITE'...                                  	No

```

furthermore the thermal-zones are changing on each booting (also when using hibernation)

```
dmesg | grep Thermal
[   16.111986] ACPI: Thermal Zone [TZ3] (24 C)
[   16.114233] ACPI: Thermal Zone [TZ4] (25 C)
[   16.115091] ACPI: Thermal Zone [TZ5] (69 C)
[   16.121694] ACPI: Thermal Zone [TZ0] (35 C)
[   16.125296] ACPI: Thermal Zone [TZ1] (34 C)
```

on the next boot it looks like this:

```

dmesg | grep Thermal
[   15.534519] ACPI: Thermal Zone [TZ3] (54 C)
[   15.537007] ACPI: Thermal Zone [TZ4] (30 C)
[   15.537956] ACPI: Thermal Zone [TZ5] (69 C)
[   15.545414] ACPI: Thermal Zone [TZ0] (60 C)
[   15.549017] ACPI: Thermal Zone [TZ1] (61 C)
```

I also reported the problem to lm-sensor's homepage, but didn't receive an answer yet.

[http://www.lm-sensors.org/ticket/2359](http://www.lm-sensors.org/ticket/2359)

Could anybody please provide me with useful tipps?

---

### Post by map84 on 2009-02-01
Meanwhile i managed to do a workaround:

using powernowd to silence the system a little more, since the sensors won't get detected by lm_sensors.

```
/etc/default/powernowd 
#default file for powernowd, see man 1 powernowd
# 
# Options
OPTIONS="-m 3 -u 95 -l 50 -p 3000 -q"
```

changing the default options of powernowd provides me with a almost silent system.

Someday the sensors could be detected by lm_sensors, if HP Compaq provide the community with the needed Datasheets.

---

### Post by dixon on 2009-02-21
Is it safe? What do those options mean? I'll try that on my 6720s as soon as I get home :)

---

### Post by map84 on 2009-04-25
> **dixon said:**
> Is it safe? What do those options mean? I'll try that on my 6720s as soon as I get home :)

The options are safe. I've never encountered a problem (e.g. overheating, shutdown of the system ect.). I upgraded to jaunty this week and I'm honoured with more silent fan's than under U8.10 now. The fan's stays on the same spin-level the whole time.

---

### Post by majikins on 2009-05-14
> **map84 said:**
> The options are safe. I've never encountered a problem (e.g. overheating, shutdown of the system ect.). I upgraded to jaunty this week and I'm honoured with more silent fan's than under U8.10 now. The fan's stays on the same spin-level the whole time.

hi

yes I am on Jaunty an I must say its a lot quieter and less heat generation that on Hardy!  However I only get cpu temperatures- no hardrive and fan information.

acpitz-virtual-0
Adapter: Virtual device
temp1:       +40.0°C  (crit = +105.0°C)                  
temp2:       +24.0°C  (crit = +108.0°C)                  
temp3:       +50.0°C  (crit = +110.0°C)                  
temp4:       +45.0°C  (crit = +256.0°C)                  
temp5:       +43.0°C  (crit = +108.0°C)                  

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +43.0°C  (high = +100.0°C, crit = +100.0°C) 

Have you managed to get this right?

---

### Post by ville_pie on 2009-07-24
I'm also struggling with HP 6720's fan and I'm not able to change the frequency of the processor or even detect sensors with lm_sensors. I can work with heat sensors. This is powernowd's output:

```
sudo /etc/init.d/powernowd start
* Starting powernowd...
* CPU frequency scaling **not supported**...                                [ OK ]
```There has been a while since you guys posted your messages. Have you solved this issue? I have searched for an answer for a few days and yet haven't found one.

BTW I'm running Jaunty.

---

