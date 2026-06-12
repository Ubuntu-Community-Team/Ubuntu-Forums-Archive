---
title: "hp6110nx fan speed problem"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by martbab on 2007-11-04
Hello everyone,

I have a problem with cooling of my CPU.

I'm using hp6110nx with Intel Celeron M 1.4 GHz processor running under Xubuntu Gutsy/WinXP and I noticed that when in Windows, my fan works just fine, having usual three speed levels, slow and mid when the load is not very high and high speed when something CPU intensive is going on.

Under Xubuntu  the fan runs only on low and mid speed and the high-speed mode never kicks in even when my CPU is on 100% for several minutes and the temperature goes up to 83 degrees C, which kinda scares me :???:

I've tried fiddling with ACPI trip points but it doesn't help :(

```
echo -n "100:90:90:70:50:40" > /proc/acpi/thermal_zone/TZ1/trip_points 
```

I'd be happy if someone could help me, I'm doing quite a lot of CPU intensive stuff under Xubuntu and don't  want my laptop to melt.

---

### Post by martbab on 2007-11-05
Anyone?

---

