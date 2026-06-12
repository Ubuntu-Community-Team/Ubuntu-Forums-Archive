---
title: "Laptop fans &amp; battery"
date: 2008-01-05
forum: Hardware &amp; Laptops
---

### Post by Maikelv on 2008-01-05
Hi there,

I just switched to ubuntu yesterday (due to the huge lack of innovation in windows, and the ridiculous price of macs). I'm loving it so far, it's not nearly as hard as I expected. 

I have one problem though. 
My laptop gets hot, my fans keep trying to cool it down, resulting in a very low battery life. I did not have this problem in windows XP nor in Vista (just to say its not a hardware issue). 
Does anyone know why this is the case ? because as I understand it, ubuntu uses less resources than windows.

Thanks :)

ps: does anyone know how to run the adobe cs3 suite with wine (or another way) ? I googled, but all I could find was CS2 and half baked solutions.

---

### Post by Maikelv on 2008-01-05
bump ? :)

---

### Post by AlesUbu123 on 2008-01-06
Can you give us output from listed commands?

```
sudo cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_cur_freq
```

```
sudo cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_available_frequencies 
```

```
sudo cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
```

Regards!

---

### Post by jonjpeterson on 2008-01-15
Bump!

---

### Post by Whiffle on 2008-01-15
What kind of laptop?

---

### Post by mobileking on 2008-01-15
whatz that BUmp ? :confused:

---

### Post by kvonb on 2008-01-15
-

---

### Post by Whiffle on 2008-01-15
When I had compiz on mine, it didn't run hotter.  At all.  He may or may not have  frequency scaling enabled, or maybe some other power management items.

---

