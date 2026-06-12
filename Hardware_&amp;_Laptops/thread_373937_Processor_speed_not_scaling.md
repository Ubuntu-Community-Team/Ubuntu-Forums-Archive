---
title: "Processor speed not scaling?"
date: 2007-03-01
forum: Hardware &amp; Laptops
---

### Post by band-aid on 2007-03-01
I don't think my T7400 Core 2 duo is scaling down when not under load correctly. When I do lshw it is constantly at the max 2.16 GHZ. In windows I can check it with RM clock and when Idle or under light load it hovers around 1 ghz and this saves battery life and lets it run cooler. How can I enable this?

---

### Post by newlinux on 2007-03-01
what do

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies
```

and

```
cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_governors
```

return?

---

### Post by band-aid on 2007-03-01
The first one gives

```

2167000 1667000 1333000 1000000

```

So the frequencies appear to be set

The other gives

```

userspace powersave ondemand conservative performance 

```

I'm guessing these are available profiles.

---

### Post by newlinux on 2007-03-01
yep. take a look at 
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_your_CPU.27s_Power_Saving.2FFrequency_Scaling_features)

That should help you get it running like you want it to... There is also a gnome applet that you can place in a toolbar that can monitor your frequency

(right click on your panel ->Add to panel...->system and Hardware

---

