---
title: "thinkpad acpi fan problem, trying to show fan speed in conky"
date: 2010-04-30
forum: Hardware
---

### Post by SnickerSnack on 2010-04-30
I have a thinkpad x61t, and I've been using
```
$ibm_fan
```
in my .conkyrc to display the fan speed.  I previously used
```
${execi 5 cat /proc/acpi/ibm/fan | grep speed | cut -c 9-12}
```
which worked just as well.

Now, neither works.  Both read '0', and while I can only see that $ibm_fan simply doesn't work, the second bit doesn't work because the file /proc/acpi/ibm/fan reads
```
status:		enabled
speed:		0
level:		auto
```

This is ubuntu 9.10, and the only changes I've made are recommended updates.

Additionally, sensors now reports a fan speed of zero, although it used to report it (presumably correctly).  sensors output:
```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +54.0°C  (crit = +127.0°C)                  
temp2:       +64.0°C  (crit = +100.0°C)                  

thinkpad-isa-0000
Adapter: ISA adapter
fan1:          0 RPM
temp1:       +54.0°C                                    
temp2:       +48.0°C                                    
temp3:       +48.0°C                                    
temp4:       +46.0°C                                    
temp5:       +36.0°C                                    
ERROR: Can't get value of subfeature temp6_input: Can't read
temp6:        +0.0°C                                    
temp7:       +35.0°C                                    
ERROR: Can't get value of subfeature temp8_input: Can't read
temp8:        +0.0°C                                    
temp9:       +48.0°C                                    
temp10:      +44.0°C                                    
ERROR: Can't get value of subfeature temp11_input: Can't read
temp11:       +0.0°C                                    
ERROR: Can't get value of subfeature temp12_input: Can't read
temp12:       +0.0°C                                    
ERROR: Can't get value of subfeature temp13_input: Can't read
temp13:       +0.0°C                                    
ERROR: Can't get value of subfeature temp14_input: Can't read
temp14:       +0.0°C                                    
ERROR: Can't get value of subfeature temp15_input: Can't read
temp15:       +0.0°C                                    
ERROR: Can't get value of subfeature temp16_input: Can't read
temp16:       +0.0°C                                    

coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +64.0°C  (high = +100.0°C, crit = +100.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +64.0°C  (high = +100.0°C, crit = +100.0°C)  
```

Ideas?  Are there any packages I should try reinstalling?

Thanks.

edit: Also, /sys/devices/platform/thinkpad_hwmon/fan1_input also reads "0".

edit2: Yes, the fan is actually running normally, it's just that none of the methods I was using to read the fan speed are working.

edit3: If I'm reading it right, then this page suggests that it is no longer possible to read fan speed through acpi: [http://www.thinkwiki.org/wiki/Ibm-acpi](http://www.thinkwiki.org/wiki/Ibm-acpi)

---

### Post by postmako on 2010-05-25
I use tpfand_0.95-ubuntu1_all.deb and tpfan-admin_0.96-ubuntu1_all.deb and they've worked well for me to see the fan speed and to change the speed depending on temperature readings from the various sensors.  I hope that helps...

I have attached the deb files mentioned above.

My /etc/tpfand.conf looks like the following:
```

enabled = True
override_profile = True

0. CPU = 0:0 15:3 20:5 35:6 50:8 65:256 
1. Mini-PCI = 0:0 15:3 20:5 35:6 50:8 60:256 
2. HDD = 0:0 15:3 20:6 35:8 42:256 
3. GPU = 0:0 15:3 20:5 35:6 50:8 65:256 
4. Battery = 0:0 15:3 20:6 35:8 40:256 
5. Sensor 5 = 0:255 
6. Battery = 0:0 15:3 20:6 35:8 40:256 
7. Sensor 7 = 0:255 
8. Sensor 8 = 0:255 
9. Sensor 9 = 0:255 
10. Sensor 10 = 0:255 
11. Sensor 11 = 0:255 
12. Sensor 12 = 0:255 
13. Sensor 13 = 0:255 
14. Sensor 14 = 0:255 
15. Sensor 15 = 0:255 

hysteresis = 2
interval_speed = 2
interval_duration = 500.000000
interval_delay = 5000.000000

```

---

### Post by SnickerSnack on 2010-05-30
Thanks, I'll have a look at that when I have time.

---

