---
title: "IBM ACPI Thermal Sensors on T61"
date: 2008-06-13
forum: Hardware
---

### Post by zro on 2008-06-13
I was wondering if anyone knew which thermal sensors are which in the temperature read out of **/proc/acpi/ibm/thermal**.

[http://www.thinkwiki.org/wiki/Thermal_Sensors](http://www.thinkwiki.org/wiki/Thermal_Sensors) doesn't seem to mention the T61 yet... so if you know, please add it there as well.

[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html) says "Sensor 0 is on the CPU, 3 is on the GPU.", but according to thinkwiki it varies in models, and what about 2x core's?

[http://ubuntuforums.org/showthread.php?p=3353521&#post3353521](http://ubuntuforums.org/showthread.php?p=3353521&#post3353521) seems to imply that 0 is CPU, 2 is HDD, and 3 is GPU... but palisaide doesn't state the model or anything. 

It would be nice to know for conky, etc...
Thanks!

```
$ cat /proc/acpi/ibm/thermal
```

---

