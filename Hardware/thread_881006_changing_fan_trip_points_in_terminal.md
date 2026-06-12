---
title: "changing fan trip points in terminal"
date: 2008-08-05
forum: Hardware
---

### Post by hcaleman on 2008-08-05
I noticed on my new install of 8.04 the fan has yet to come on in my laptop.  Temps are sitting around 45-52C.  I ran cat /proc/acpi/thermal_zone/THRM/trip_points and came up with following:

cat /proc/acpi/thermal_zone/THRM/trip_points
critical (S5):           97 C
passive:                 96 C: tc1=9 tc2=2 tsp=1800 devices=CPU0 
active[0]:               96 C: devices= FAN 
active[1]:               96 C: devices= FAN 

I think the temperature settings are a bit ridiculous for the active states so would like to adjust them down a bit.  From what I gathered from searching around a bit I need to run the following to adjust the trips:

echo -n  "65:0:60:55:50" > /proc/acpi/thermal_zone/THRM/trip_points

this spits out a write error: input/output error.  Are the points not adjustable for some reason, or am I going about this the wrong way?

---

### Post by rustamb on 2008-08-17
I have the same problem. Didn't find any solution yet. I guess in order to set these params your kernel must be aware of your fan. Could you check you /proc/acpi/fan. Mine is empty. If it's empty then kernel did not recognize cpu fan, and probably this is the reason why we cannot set the value for this parameter. If this is the case then my question to community is: how can we tell kernel about cpu fan?

I use ubuntu 8.04.1 ( 2.6.24-19-generic) on HTC Shift X9500 (it's umpc)

Thanks.

---

