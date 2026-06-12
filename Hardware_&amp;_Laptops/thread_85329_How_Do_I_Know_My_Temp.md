---
title: "How Do I Know My Temp?"
date: 2005-11-02
forum: Hardware &amp; Laptops
---

### Post by Breezy Badger on 2005-11-02
Hello,

I noticed since I installed linux on my dell latitude C600 that the fan never comes on in the back now.  I might be making something of nothing (perhaps its just not getting hot enough) but how to I make sure that the cpu fan is working and my chip is not going to fry.

also is there a way to check and see if my cpu is running at the right freq, when it was installing I had some windows that said cpufreq: change failed with new_state 0 and result 0, it didnt do anything, the install kepts running, but I guess im just getting paranoid

Badger

---

### Post by towsonu2003 on 2005-11-02
[QUOTE=Breezy Badger]Hello,

I noticed since I installed linux on my dell latitude C600 that the fan never comes on in the back now.  I might be making something of nothing (perhaps its just not getting hot enough) but how to I make sure that the cpu fan is working and my chip is not going to fry.[/QUOTE]

To get the temperature, in a terminal, I do 

Corrected a little bit --> cat /proc/acpi/ther [press tab here]/ [Press tab here]/temp [press tab here]

[EDIT] 

Was wrong path above, should have been:

> 
cat /proc/acpi/thermal_zone/THM0/temperature


Thanks Flandry :)

[/EDIT]


[press tab here] means I press tab for it to complete the line. I dont remember exact names of the folders...

It works in my laptop, hp pavilion.

---

### Post by Breezy Badger on 2005-11-02
thanks for the reply man but its a no go, unless you may hvae typed something in wrong

---

### Post by Flandry on 2005-11-02
On my Thinkpad it's 
cat /proc/acpi/thermal_zone/THM0/temperature

Currently at 45oC, apparently.

---

### Post by towsonu2003 on 2005-11-02
[QUOTE=Breezy Badger]thanks for the reply man but its a no go, unless you may hvae typed something in wrong[/QUOTE]

typed wrong, sorry.

Corrected post, as Flandry mentions above.

PS. My temp varies between 45-59C

---

### Post by RSX311 on 2005-11-02
Try out this How To for installing lm-sensors, works great for me

[http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lm+sensors](http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lm+sensors)

```
rsx@synergy:~/downloads$ sensors
w83627thf-isa-0290
Adapter: ISA adapter
VCore:     +1.64 V  (min =  +1.93 V, max =  +1.93 V)       ALARM
+12V:     +12.71 V  (min = +10.82 V, max = +13.19 V)
+3.3V:     +3.10 V  (min =  +3.14 V, max =  +3.47 V)       ALARM
+5V:       +5.01 V  (min =  +4.75 V, max =  +5.25 V)
-12V:     -14.91 V  (min = -10.80 V, max = -13.18 V)
V5SB:      +5.08 V  (min =  +4.76 V, max =  +5.24 V)
VBat:      +3.02 V  (min =  +2.40 V, max =  +3.60 V)
fan1:        0 RPM  (min = 20454 RPM, div = 2)
CPU Fan:     0 RPM  (min =   -1 RPM, div = 2)
fan3:        0 RPM  (min = 225000 RPM, div = 2)
M/B Temp:    +30Â°C  (high =   +32Â°C, hyst =  -112Â°C)   sensor = thermistor   
CPU Temp:  +31.0Â°C  (high =   +80Â°C, hyst =   +75Â°C)   sensor = thermistor   
temp3:     +16.5Â°C  (high =   +80Â°C, hyst =   +75Â°C)   sensor = diode        
vid:      +0.000 V  (VRM Version 9.0)
alarms:   Chassis intrusion detection                      ALARM
beep_enable:
          Sound alarm disabled

eeprom-i2c-0-51
Adapter: SMBus nForce2 adapter at 4c00
Memory type:            DDR SDRAM DIMM
Memory size (MB):       512

eeprom-i2c-0-50
Adapter: SMBus nForce2 adapter at 4c00
Memory type:            DDR SDRAM DIMM
Memory size (MB):       512


```

---

### Post by Breezy Badger on 2005-11-02
thanks fellas

---

### Post by edal on 2005-11-08
From a terminal screen type:

acpi -V

Note that the 'V' is a capital letter.

Ed Almos

---

### Post by wezlo on 2005-11-08
[QUOTE=edal]From a terminal screen type:

acpi -V

Note that the 'V' is a capital letter.

Ed Almos[/QUOTE]

Anyone ever have the problem when acpi always says your processor temp is 0, no matter what?

---

### Post by ddonky on 2006-02-24
[QUOTE=edal]From a terminal screen type:

acpi -V

Note that the 'V' is a capital letter.

Ed Almos[/QUOTE]


Type:

acpi -Vf 

for temp in degrees F.

---

### Post by wezlo on 2006-02-24
[QUOTE=ddonky]Type:

acpi -Vf 

for temp in degrees F.[/QUOTE]

That's the problem, it always says 0 or 32 depending on which measurement I'm trying to use..

---

### Post by Tamale on 2006-04-01
ok, this works great - but what'd be an easy way to get a constant display of the temperature on a panel?

---

