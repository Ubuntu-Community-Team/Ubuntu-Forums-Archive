---
title: "Average Operating Temperature"
date: 2009-08-22
forum: Hardware
---

### Post by hackerseraph on 2009-08-22
[FONT="Arial"][SIZE="2"]I've been reading through pdf upon pdf looking up the normal operating temperature for the Atom n270 processors. [COLOR="Blue"]Anyone know of any sites that collect anonymous statistics so I can see what most people with the same processor are pulling as far as temperature goes.[/COLOR]Intel's pdf for the n270 shows catastrophic processor temperature of 125°C but no operating temperature range and storage temperatures are useless in this case.

I'm current showing 

```

marcus@marcus-laptop:~$ sensors
acpitz-virtual-0
Adapter: Virtual device
temp1:       +56.0°C  (crit = +85.0°C)                  

eeepc-virtual-0
Adapter: Virtual device
fan1:       1024 RPM

```

But I pulled 80 °C last night and i can tend to run up to the mid 60s on a normal basis. I merely want to see what everyone else is getting.[/SIZE][/FONT]

---

### Post by SoftwareExplorer on 2009-08-22
> **hackerseraph said:**
> [FONT=Arial][SIZE=2](crit = +85.0°C)[/SIZE][/FONT]
Thats probably a good clue as to what is OK. I know when I built my desktop I was quite worried about CPU temp, and then eventually got over it.

---

### Post by hackerseraph on 2009-08-22
> **SoftwareExplorer said:**
> Thats probably a good clue as to what is OK. I know when I built my desktop I was quite worried about CPU temp, and then eventually got over it.

I wanted to go by that, but 
```

marcus@marcus-laptop:~$ sudo sensors-detect
[sudo] password for marcus: 
# sensors-detect revision 5249 (2008-05-11 22:56:25 +0200)

```

showed that lm-sensors is practically useless because it can't register any sensors for my asus mainboard and n270 processor. (just displays no's) I dont even know how accurate that temp reading is nor the critical temp and I know the critical temp is at least above 90 per intel's pdf, just thinking on the extreme side of things, i merely wanna see  what others are pulling. I browsed cpu-z' site for a list or something.

---

### Post by hackerseraph on 2009-08-22
Heres a log file of my stressing the crud out of my unit. Compiz effects like crazy (snow, rain, cursor location), videos, music, desktop cube, google earth, etc etc. touched the low 70s. I did see that 80 for a split second when I had the unit on my lap on a book and I know the rule, never use a laptop on your lap. But like I said, im not so worried about it overheating as I just want to see what peoples normal temps are.

---

