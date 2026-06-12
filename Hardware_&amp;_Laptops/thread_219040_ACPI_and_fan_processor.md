---
title: "ACPI and fan processor"
date: 2006-07-19
forum: Hardware &amp; Laptops
---

### Post by tonyo46 on 2006-07-19
Hello

I have some problems with my acpi.
After a moment, my cpu fan doesn't turn and the temperature of my cpu increase very fast !
I read some documentations on internet about acpi and I notice that I have something quite strange on my laptop.
When I run this command :
$ cat /proc/acpi/thermal_zone/THRM/trip_points
critical (S5):           95 C
passive:                 85 C: tc1=2 tc2=3 tsp=50 devices=0xc14e9460

I don't have any "active[0]" temperature defined...
I read that it corresponded to the temperature to which the fan starts turning... so that could explane why it doesn't turn on my laptop...

How can I indicate to the system this temperature ?
How can I re-configure acpi ? (as it worked well two weeks before)

Anybody can help ?

Thank you
tonyo

---

