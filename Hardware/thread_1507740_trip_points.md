---
title: "trip_points"
date: 2010-06-12
forum: Hardware
---

### Post by CylnZ on 2010-06-12
I want to run 

```
sudo echo -n 70:65:35:60:55:50:45:40 > /proc/acpi/thermal_zone/TZS0/trip_points
```
I receive this error:

```
bash: /proc/acpi/thermal_zone/TZS0/trip_points: Permission denied
```Is it, or is it not possible to edit or echo your acpi values in ubuntu anymore?

I followed this **[tutorial]("http://ubuntuforums.org/showthread.php?t=379729")** EXACTLY to no effect.

Yes, I have completely cycled the system. 

**[COLOR=Red]$ cat /proc/acpi/thermal_zone/*/*[/COLOR]**

<setting not supported>
<polling disabled>
state:                   ok
temperature:             43 C
critical (S5):           100 C
passive:                 97 C: tc1=0 tc2=50 tsp=0 devices=CPU0 CPU1 
<setting not supported>
<polling disabled>
state:                   ok
temperature:             45 C
critical (S5):           110 C
passive (forced):<not set>

Still at it's default values. :(

I've been running my laptop on top of 4 dice with a fan for over a year now. That way it stays between 40 and 55 C even under heavy gaming. I've tried 3 different cooling pads and they're pretty much garbage. It's a PORTABLE. If i have to bring the desk with me for the system not to burn up, it's not really mobile, is it?

Yes, it's clean. It's been torn completely down to bare chassis several times in the last year. Yes, both fans have been replaced with server grade ball bearing fans. Yes, I was running a perfectly good DSDT file I fixed up from a tutorial by 67GTA with 0 errors, until upstream decided I shouldn't get to have a error-less setup. Yes, i am running the latest BIOS. No, there arent ANY power management or fan settings in it.

No, nothing has worked. I had real hope for this idea of just 
TELLING THE COMPUTER WHAT TEMPS I WANTED TO WORK WITH.

Honestly, if the system ever hits 70C I'll hard power it off, let alone allow it to see 97C.
That's absurd.

---

