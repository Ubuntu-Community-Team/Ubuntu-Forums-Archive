---
title: "Very Bad Inspiron 6000 Battery Life"
date: 2008-11-07
forum: Hardware
---

### Post by poosenki on 2008-11-07
Hi, I've been using Hardy on a Dell Inspiron 6000 for awhile now, and I've always gotten rather poor battery life. I figured it was just because I have had my batteries around for a couple years, but I just bought a brand new one and put it in the other day, and it's still low.

I've heard around that after buying the same sort of 80 WHr 9-Cell Lithium-Ion battery, people running XP get around 4 hours of life whereas I get around 2. It's pretty disappointing. Is there anything that I can maybe try to get the most out of the battery?

Thanks very much in advance!

---

### Post by jimv on 2008-11-07
Well, you could turn of Desktop Effects if you have that on, and run your screen a bit dimmer when the laptop is not plugged in.  Also, check to see if you have some rogue process running in the background that is running the CPU constantly.

AND

You can use the CPU monitor applet to control the speed of your CPU (should be doing it automatically, but you never know).

---

### Post by mylinuxs on 2009-07-21
> **poosenki said:**
> Hi, I've been using Hardy on a Dell Inspiron 6000 for awhile now, and I've always gotten rather poor battery life. I figured it was just because I have had my batteries around for a couple years, but I just bought a brand new one and put it in the other day, and it's still low.

I've heard around that after buying the same sort of 80 WHr 9-Cell Lithium-Ion battery, people running XP get around 4 hours of life whereas I get around 2. It's pretty disappointing. Is there anything that I can maybe try to get the most out of the battery?

Thanks very much in advance!
check the battery is really 80Wh (also capacity 7200mah) or not, check those battery cells are new or not
Prolong the dell inspiron 6000 battery life: tips at 
[http://www.sales-battery.com/laptop-batteries/dell-inspiron-6000.htm  ]("http://www.sales-battery.com/laptop-batteries/dell-inspiron-6000.htm")

---

### Post by bacil on 2009-07-21
Look in to battery info 

```
cat /proc/acpi/battery/BAT1/info
```

and its current state

```
cat /proc/acpi/battery/BAT1/state
```

this should tell you what you have

---

