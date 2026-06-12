---
title: "Laptop temperature problems"
date: 2011-10-28
forum: Hardware
---

### Post by Atomic-Fanboy on 2011-10-28
I'm having temperature problems with my laptop computer ( Acer Aspire 5332 - Celeron dual core 1.8 GHz T3000, 3GB RAM, integrated graphics processor GMA 4500M).

When I switch it on, the processor temperature is about 28 to 30 degrees (where it should be). However it increases VERY rapidly to between 60 and 80 degrees, often higher - occasionally as high as 102 degrees. 

The hard disk often heats to between 60 and 70 degrees as well.

Does anyone know the critical temperature for these components ( sensors reports a critical CPU temperature of 110, but I'm not sure if that's right.)

Also, does anyone know a way of cooling it down - I would increase fan speed, but I don't think my laptop has fan sensors.

Thanks :)

---

### Post by Lars Noodén on 2011-10-28
I've been having similar problems with the machine getting way to hot and the fan not running even when it gets hot:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/881593](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/881593)

From hardware specs on single board computers and lot of network devices, I would expect that 50C - 60C is the safe max.  Obviously cooler is better for the life of the machine.

In addition to the machine in the above bug report, I'm finding that another machine also appears to be overheating.

---

### Post by Atomic-Fanboy on 2011-10-28
*Shudder*

Thanks for answering, but a safe max of 50 to 60 is quite worrying.

---

### Post by Atomic-Fanboy on 2012-03-01
This is not a problem for me now, I've moved to Fluxbox :D

---

### Post by ampcook on 2012-03-27
I'm running Ubuntu 11.10 and had problems of temperature in my laptops Acer Aspire 5551-4873 and LG LGR 40. Problems were even in other version Linux. My approach to the solution was installing indicator-cpufreq from

[http://www.noobslab.com/2011/07/cpu-frequency-scaling-indicator-on.html](http://www.noobslab.com/2011/07/cpu-frequency-scaling-indicator-on.html). 

The solution is to slow down the frequency, not to measure the temperature and see how hot the notebook  is. I reduce temperature in 10 C using Powersave mode. I can't tell a difference in performance, at less with my eyes. I prefer a notebook running slower (and it is not the case) to burning.

---

### Post by Mark Phelps on 2012-03-29
ampcook: While I'm glad to see you found a "solution", I think most folks here would rather get the performance out of their notebook that they paid for -- rather than force it to run slower.

Not criticising what you did; I understand your approach.

Just saying that it's a sad state of affairs when we have to do without performance we paid for to prevent our laptops from burning out.

---

