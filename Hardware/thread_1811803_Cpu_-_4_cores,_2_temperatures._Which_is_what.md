---
title: "Cpu - 4 cores, 2 temperatures. Which is what ?"
date: 2011-07-25
forum: Hardware
---

### Post by luceerose on 2011-07-25
My Samsung RC720 laptop has an intel Quad core.
After a sensors-detect ,
sensors shows;
```
acpitz-virtual-0
Adapter: Virtual device
temp1:        +45.0°C  (crit = +100.0°C)
temp2:        +29.8°C  (crit = +100.0°C)

coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +46.0°C  (high = +86.0°C, crit = +100.0°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 1:       +46.0°C  (high = +86.0°C, crit = +100.0°C)
```
From what I can tell, temp1 is composed of both Core 0 & Core 1.
And temp2 must be something on the motherboard, like the NB or GPU.

I've been able to show these in my Conky script with;
```
${hwmon 0 temp 1}${hwmon 1 temp 1}
${hwmon temp 2}
```
But I still don't know what these temperatures represent...

#Numbering the cpu's cores 1-4#...
Have I only been given the temperatures for core 1 & 2 whilst 3 & 4 are ignored ?
Or do the temperatures represent two cores at once, say,
(1+2) and (3+4) ?
Or (1+3) and (2+4) ?

Can anyone enlighten me ?

---

### Post by dabl on 2011-07-25
Which Intel CPU?  AFAIK, there should be one thermal sensor for each core.  Here is the relevant output of "sensors" for my i7-950 on an Asus P6X58D-E motherboard:


```
coretemp-isa-0000
Adapter: ISA adapter
Core 0:       +40.0°C  (high = +80.0°C, crit = +100.0°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:       +35.0°C  (high = +80.0°C, crit = +100.0°C)

coretemp-isa-0002
Adapter: ISA adapter
Core 2:       +39.0°C  (high = +80.0°C, crit = +100.0°C)

coretemp-isa-0003
Adapter: ISA adapter
Core 3:       +35.0°C  (high = +80.0°C, crit = +100.0°C)
```

---

### Post by .... on 2011-07-25
> My Samsung RC720 laptop has an intel Quad core.
No, it has a dual-core with Hyper Threading, which presents itself as 4 virtual cores. [http://ark.intel.com/products/52224/Intel-Core-i5-2410M-Processor-%283M-Cache-2_30-GHz%29](http://ark.intel.com/products/52224/Intel-Core-i5-2410M-Processor-%283M-Cache-2_30-GHz%29)
So you should have only two core temps.

---

### Post by dabl on 2011-07-25
OK, dual core = 2 real cores, and therefore 2 thermal sensors.  So yours is working right. The hyperthreading allows one core to run 2 parallel processes, so it presents itself to Linux as 4 processors, but in fact there are really only 2.

FYI, my i7-950 puts up 8 penguins when I boot it.  :D

---

### Post by luceerose on 2011-07-26
Aha.
Thank You.
I originally thought it was a Dual-Core. Once I got everything installed I was surprised to find 4 cores showing up in System Monitor.
Now I understand why.

Coincidently, I have an AMD Six-Core which presents itself as Six cores with Six threads & only gives me 1 temperature.
I guess intel do things differently.

This laptop is actually the first intel chip I've owned since the Pentium 3 days.

---

