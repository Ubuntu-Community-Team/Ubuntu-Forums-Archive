---
title: "fan going crazy with normal temperature [solved]"
date: 2020-04-25
forum: Hardware
---

### Post by darko5 on 2020-04-25
Hi all !

I don't know if I'm posting in the right thread, if not tell me.

I have a problem since this morning with my laptop (Lenovo T430), with a system installed for one year without problem. I didn't update anything last night, and I have never tried to tweak anything concerning the temperature/fan.

My system :
```
[FONT=monospace][COLOR=#000000]Ubuntu 19.04 \n \l[/COLOR]

[/FONT]
```

I installed sensors and I got this output :
```
[FONT=monospace][COLOR=#54FF54]**darko@pollux**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ sensors        [/COLOR]
thinkpad-isa-0000
Adapter: ISA adapter
fan1:        3154 RPM

acpitz-acpi-0
Adapter: ACPI interface
temp1:        +46.0°C  (crit = +104.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +46.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:        +46.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:        +43.0°C  (high = +87.0°C, crit = +105.0°C)

[/FONT]
```

The temperatures seem normal to me, I don't know, and yet the fan is going full speed. Don't know what to do, does anyone have an advice ?

---

### Post by CelticWarrior on 2020-04-25
First of all you need to upgrade to a supported release. 19.04 is out of support since January. The upgrade should be done regardless of any other problem.
Then, if the symptom persists, troubleshoot from there. that said, it's likely hardware related. Cleaning the vents is probably a good idea.

---

### Post by darko5 on 2020-04-25
> [COLOR=#000000]First of all you need to upgrade to a supported release.[/COLOR]
You're right ! I did it, but the problem is still here.

I got this now 
```
[FONT=monospace][COLOR=#54FF54]**darko@pollux**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454FF]**~**[/COLOR][COLOR=#000000]$ sensors[/COLOR]
thinkpad-isa-0000
Adapter: ISA adapter
fan1:        3205 RPM
temp1:        +46.0°C   
temp2:         +0.0°C   
temp3:         +0.0°C   
temp4:         +0.0°C   
temp5:         +0.0°C   
temp6:         +0.0°C   
temp7:         +0.0°C   
temp8:         +0.0°C   

BAT0-acpi-0
Adapter: ACPI interface
in0:         +12.51 V   

coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +47.0°C  (high = +87.0°C, crit = +105.0°C)
Core 0:        +47.0°C  (high = +87.0°C, crit = +105.0°C)
Core 1:        +43.0°C  (high = +87.0°C, crit = +105.0°C)

acpitz-acpi-0
Adapter: ACPI interface
temp1:        +46.0°C  (crit = +104.0°C)

[/FONT]
```

But about this cleaning the vents thing, you mean from  outside ?

---

### Post by darko5 on 2020-06-30
It was a hardware breakdown actually. I ended up getting "fan error" at boot, and well no boot. I had the fan changed, et everything is back to normal.

---

