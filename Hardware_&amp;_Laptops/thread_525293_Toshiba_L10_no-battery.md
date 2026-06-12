---
title: "Toshiba L10 no-battery"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by depele on 2007-08-14
Hello, 

I have a Toshiba Satellite L10 
Ubuntu feisty linux-headers-2.6.20-16 os.

```
/proc/acpi/battery 
``` ==> has no subdirectory's

```
sudo rmmod acpi_sbs
sudo rmmod battery
sudo modprobe battery
``` ==> no result
```

root@ubuntu:/usr/src# sudo acpi -V
     Thermal 1: ok, 54.0 degrees C
``` ==> no battery



I have been looking around for about 3 day's now and I still can't get it to work. 

[https://help.ubuntu.com/community/ACPIBattery]("https://help.ubuntu.com/community/ACPIBattery")

I have tried a tutorial from gentoo ==> nothing
another one on a french site etc... 
But still no work.

Please help me.

grtz... 

Arne

output of dmesg attached to this post

---

### Post by depele on 2007-08-14
nobody with a solution or the same problem?

grtz..

---

### Post by depele on 2007-08-19
bump

---

### Post by depele on 2007-08-20
bump *2

---

### Post by saj0577 on 2007-08-22
i got same problem mate same laptop it is the latest security update sthat have messed up our acpi settings, i am currently looking for someone to help me recompile my kernel with the acpi from the version before the security updates came in that messed it up. IF i get it sorted i will right a sep by step guide for you and everyone else with similar problem.

Saj

---

### Post by depele on 2007-08-23
Thanks a lot.

I hope you will get a sollution.


grtz..

Arne

---

