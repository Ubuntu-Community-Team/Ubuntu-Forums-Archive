---
title: "inconsistent trip_points: same hardware, different values"
date: 2011-01-15
forum: Hardware
---

### Post by stn21 on 2011-01-15
Hi,

what is this? I have two laptops Fujitsu-Siemens Amilo M 7440, both running Ubuntu 10.10.

One shows this:

```
# cat /proc/acpi/thermal_zone/THRM/trip_points 
critical (S5):           105 C
passive:                 86 C: tc1=3 tc2=1 tsp=150 devices=CPU0 
active[0]:               65 C: devices= FN1 
active[1]:               50 C: devices= FN2
```The other this:

```
# cat /proc/acpi/thermal_zone/THRM/trip_points 
critical (S5):           85 C
passive:                 74 C: tc1=3 tc2=1 tsp=150 devices=CPU0 
active[0]:               64 C: devices= FN1 
active[1]:               50 C: devices= FN2
```The second one often shuts down unexpectedly, syslog says "critical temperature reached". 

Obviously that is because its critical temperature is 85 C, while the other one allow up to 105 C. Where does this low "critical" value come from and how can I change it? It is really annoying if the computer shuts down right in the middle of some Makefile :(

THX

---

### Post by gordintoronto on 2011-01-15
Sorry, I can't answer your question.

However, I suggest you should be asking, "how can I get the fans running so the computer does not get so outrageously hot?"

I would begin by installing lm-sensors.

---

### Post by stn21 on 2011-01-16
> **gordintoronto said:**
> Sorry, I can't answer your question...
True

Anyone with useful comments ?

THX

---

### Post by stn21 on 2011-01-16
.

---

