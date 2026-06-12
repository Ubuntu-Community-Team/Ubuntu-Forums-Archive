---
title: "What is normal CPU temperature?"
date: 2005-12-16
forum: Hardware &amp; Laptops
---

### Post by risager on 2005-12-16
I have a Toshiba Laptop M35-s456 with a 1.7 Pentium M processor. ```

morten@toshiba:~$  cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.70GHz
stepping        : 6
cpu MHz         : 598.591
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe est tm2
bogomips        : 1188.32


```

Does anyone know what is considered the correct working temperature for this kind of CPU? It runs 60-65C on light use and 65-75C on heavy use. I see other people in this forum that talks about temperatures around 40-50C.

---

### Post by az on 2005-12-16
[QUOTE=risager] I see other people in this forum that talks about temperatures around 40-50C.[/QUOTE]

For that laptop or in general.  Because acceptable temperature is very much dependant on the type of processor and the model of laptop.

You can look up the ideal temperature on the manufacturer (intel) website.

I googled:

[http://support.intel.com/support/processors/mobile/pm/sb/CS-007971.htm](http://support.intel.com/support/processors/mobile/pm/sb/CS-007971.htm)

and from another site:
"Intel Pentium 4, Pentium 4 Extreme Edition, Pentium M
 

Pentium 4
Max. temperature depends much on model and clockspeed, but no clear pattern is visible. Consult Intel's tech specs for information on your particular model.
(Lowest: P4 Extreme Edition 3.2GHz with 64&#176;C, highest: P4 Willamette 1.8GHz with 78&#176;C).  64&#176;C - 78&#176;C 
Pentium M
 100&#176;C (!)"

---

### Post by raghav_p on 2005-12-17
For your processor (and mine) the maximum temperature is 100C. I usually run around 30C when I'm working on my desk (at lowest clock speed) and perhaps around 45-50 on my desk (at highest clock speed). When watching a movie or something on my bed, it's usually around 45C at lowest clock speed.

Just giving reference ;-)

---

### Post by eraclito on 2005-12-17
in my laptop:

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 9
model name      : Intel(R) Pentium(R) M processor 1500MHz
stepping        : 5
cpu MHz         : 600.156
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe est tm2
bogomips        : 1189.47

i usually stay at 40- 45C
with an intense use (kernel compilation) i reach 60c

eraclito

---

### Post by drummer on 2005-12-17
holy crud monkeys!!... my desktop runs at 25 idle and the highest I've seen it get is about 43 after about an hour of gaming (full cpu use). This is an athlon64 3000. A friend of mine says his athlonXP gets to 80 and I'm surprised the core doesn't melt (!!) :P

I guess that just shows that there can be such variation depending on the chip.. and probably the system and cooling efficiency also.

EDIT - sorry, i know this is in the laptop forum.. just felt i needed to express my surprise.

---

