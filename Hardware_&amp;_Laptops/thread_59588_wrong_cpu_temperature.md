---
title: "wrong cpu temperature"
date: 2005-08-24
forum: Hardware &amp; Laptops
---

### Post by pau on 2005-08-24
Hi,

i have a bug...

I have been trying to find out like an idiot during days why my fan is running all the time and
I have found out now that 

```
/proc/acpi/thermal_zone/THRM/temperature
```

is fixed to 75º

This is wrong, because the air being blown out is not really hot... and the laptop itself 
is not very hot... 
As a matter of fact, I installed  KSensors which is basically lm-sensors with a gui interface and I
found out that the current temperature was showing 75º but in grey... 

I think that ubuntu is not upgrading the value or giving it wrong so that the fan is running all
the time wven thought the laptop is not really hot...

any idea of how could I fix this??  ](*,)

---

