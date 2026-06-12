---
title: "Power settings on IBM laptop"
date: 2006-01-15
forum: Hardware &amp; Laptops
---

### Post by cucamelsmd15 on 2006-01-15
Ive got Klaptop running, but plugged or unplugged, cat /proc/cpuinfo yeilds this:

> processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 9
model name      : Intel(R) Pentium(R) M processor 1600MHz
stepping        : 5
cpu MHz         : 1598.681
cache size      : 1024 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 tm pbe est tm2
bogomips        : 3170.30

Any suggestions on how to slow the processor down? It chews a battery in about two hours like this. Id also like to get it below 600Mhz if possible.

---

### Post by lisje on 2006-01-15
try install the powernowd:
```
sudo apt-get install powernowd
```

it should slow the processor down if your laptop can speedstep.
greets,
Lisje

---

### Post by cucamelsmd15 on 2006-01-16
[QUOTE=lisje]try install the powernowd:
```
sudo apt-get install powernowd
```

it should slow the processor down if your laptop can speedstep.
greets,
Lisje[/QUOTE]

Ive got that installed, but it sets the processor speed as either 600mhz or 1.6ghz. It never changed no matter if its plugged or unplugged. How do I change it?

---

### Post by cucamelsmd15 on 2006-01-17
Ok, cat /proc/cpuinfo gives me the same thing despite being plugged or unplugged. Does this mean that its not working?

---

### Post by lisje on 2006-01-17
I've had the same problem I think... I had powernowd running on a dell latitude d600 and it didn't care whether I was working on just battery or plugged in.. the speed only changed when I opened an application like openoffice and such... so it did work .. it only didn't detect whether I was on battery or not... I know that when I tried gentoo I needed to edit a config to make powernowd fit my needs .. but with ubuntu I don't know

maybe someone else can help?

---

### Post by Miguel on 2006-01-17
AFAIK, the CPU frequency policy (in english: how to change the speed) used by default in ubuntu is the following:
[list][*]By default, stay at minimum speed (600MHz in Sonoma, 800 in Dothan)
[*] If CPU usage rises above 80%, pump the CPU to max clock speed inmediately.
[*] If CPU usage is lower than 20% after two seconds, decrease the speed one level (i.e. from 1.7 GHz to 1.5GHz) and so on. 
[/list]

This policy can be changed, so that the clock decrease is also instantaneous, or that the rise is stepped or anything in between. For more information, call 1-800-CPUFREQ... I am a bit funny today. If you want more information, have a look at

$ man powernowd

Hope it helps

---

