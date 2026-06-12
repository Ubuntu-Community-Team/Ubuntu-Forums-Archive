---
title: "ACPI: Unable to turn cooling device  'on'"
date: 2008-02-16
forum: Hardware &amp; Laptops
---

### Post by adfrui on 2008-02-16
I've seen this posted a few times and Googled a bit, but I'm still uncertain about what to do.

I was reading a thread here:

[http://www.centos.org/modules/newbb/viewtopic.php?topic_id=8158](http://www.centos.org/modules/newbb/viewtopic.php?topic_id=8158)

It says, which seems wrong:

root@TRASH:/home/owner# cat /proc/acpi/thermal_zone/THRM/*
0 - Active; 1 - Passive
polling frequency:       2 seconds
state:                   passive 
temperature:             53 C
critical (S5):           100 C
passive:                 -248 C: tc1=4 tc2=3 tsp=60 devices=CPU0 
active[0]:               -266 C: devices= FAN 



The computer is an HP a720n with an AMD Athlon XP+.  The fans are spinning rather slowly at a constant rate and don't speed up, despite the CPU getting past 55. 

Do I need to change the state to "active" and the trip points, and if so, how?  Thanks.

---

### Post by 444 on 2008-02-16
I wouldn't worry unless it started overheating. (ie 80+)

---

### Post by pt_lam on 2008-02-17
Similar problem with me.

The fan is off for most of the time, only on  for a few seconds when the temp > 50. The temp then falls to 30-40, and the fan is off again.

It sounds not very bad, but I can always feel my laptop hot through my hands, at least it won't be the case when I'm in Windows.

Anyone can help please?

---

### Post by 444 on 2008-02-17
Well there is sometimes manual fan control available in /proc/acpi, so you can turn the fan on earlier.

Another reason it might feel hot is powersaving not being enabled on the GPU, if you have a discrete one.

---

