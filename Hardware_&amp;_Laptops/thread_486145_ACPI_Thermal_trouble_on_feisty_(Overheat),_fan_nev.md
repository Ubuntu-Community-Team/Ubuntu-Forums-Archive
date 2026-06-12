---
title: "ACPI Thermal trouble on feisty (Overheat), fan never start."
date: 2007-06-27
forum: Hardware &amp; Laptops
---

### Post by jmaryinchina on 2007-06-27
What ever I am doing with my laptop (Compaq evo N160) the temperature is locked to 47°C and the fan never start.
At googling I saw peoples having the same trouble but I didn't find any solution

Everything was fine with Edgy. 
I suspect a kernel trouble so i upgraded to the one of gutsy (2.6.22) but nothing improved.

I also tried to install lm-sensors, sensors-detect goes fine and ask to insert this : 
[INDENT][I]# I2C adapter drivers
i2c-i801
# Chip drivers
eeprom[/I][/INDENT]

But after at running :
[INDENT][I]root@takaware:/dev# sensors
No sensors found!
Make sure you loaded all the kernel drivers you need.
Try sensors-detect to find out which these are.[/I][/INDENT]

Here follows the values in /proc/acpi/thermal_zone/TZO/
[INDENT][I]cooling_mode : <setting not supported>
polling_frequency : <polling disabled>
state:                   ok
temperature:             47 C
critical (S5):           100 C
passive:                 98 C: tc1=0 tc2=1 tsp=150 devices=CPU0[/I][/INDENT]

Also the direcory /proc/acpi/fan is always empty.

I'm now out of ideas.

---

