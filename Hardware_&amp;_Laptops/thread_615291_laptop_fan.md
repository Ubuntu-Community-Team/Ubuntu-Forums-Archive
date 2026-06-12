---
title: "laptop fan"
date: 2007-11-16
forum: Hardware &amp; Laptops
---

### Post by deez on 2007-11-16
I'm running an HP nc4010 on Gusty.  The CPU fan is always on.  Sometimes it slows down, but it's always on.  Doesn't seem right to me.  Any ideas?  Peace

---

### Post by dralokyn on 2007-11-17
have you checked your acpi settings?

---

### Post by paulhurleyuk on 2007-11-17
Try checking if your laptop rpeorts temperatures.  You can do that via a system logger (I use KDE, so for me it's KSysGuard) or in a terminal try

```
cat /proc/acpi/thermal_zone/*/*
```

That should list the current thermal info about your system.  You can also try

```
cat /proc/acpi/fan/*/*
```

which will list the status(es) of any system fans

Paul.

---

### Post by deez on 2007-11-17
I'm not sure how to check acpi settings, but I do know that it's active.  

here's what those commands give me, but I don't know what to do with the information.  Cheers

state:                   active[3]
temperature:             44 C
critical (S5):           103 C
passive:                 100 C: tc1=1 tc2=2 tsp=100 devices=CPU0 
active[0]:               80 C: devices=C1F6 
active[1]:               65 C: devices=C1F7 
active[2]:               52 C: devices=C1F8 
active[3]:               40 C: devices=C1F9 
<setting not supported>
<polling disabled>
state:                   ok
temperature:             36 C
critical (S5):           103 C
<setting not supported>
<polling disabled>
state:                   ok
temperature:             26 C
critical (S5):           103 C
passive:                 53 C: tc1=1 tc2=2 tsp=300 devices=CPU0 
dennis@Delphi:~$ cat /proc/acpi/fan/*/*
status:                  off
status:                  off
status:                  off
status:                  on

---

### Post by dralokyn on 2007-11-17
based on that information, your fan is on because your cpu is hot. you can set the temperature at which the fan switches on to a higher temperature, but i don't recommend it; this will probably end up burning out your processor.

---

### Post by deez on 2007-11-18
Do you know how I can do that?

---

### Post by neilevan814 on 2008-07-21
cat /proc/acpi/thermal_zone/*/*
0 - Active; 1 - Passive
<polling disabled>
state:                   ok
temperature:             44 C
critical (S5):           95 C
passive:                 88 C: tc1=2 tc2=3 tsp=100 devices=CPU0 

I checked this because my fan has not turned on in a long time and was wondering if anyone could tell me what polling disabled means and if I should turn that on for more information or not.
Thanks, Neil

---

