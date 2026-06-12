---
title: "Benchmark AMD Athlon(tm) 64 X2 Dual Core Processor 4400+"
date: 2009-12-21
forum: Hardware
---

### Post by User3k on 2009-12-21
I am curious about something. From what I udnerstand is a dual core CPU says, for example my AMD one, that it is a 2200 MHz, then that number is the total of both cores. When I run sysinfo or other benchmark programs it is saying it is only 1000.000 MHz per core. Is this becuase it is just rounding it off rather then saying 1100.00 MHz each?

---

### Post by lavinog on 2009-12-21
edit: it is because of freq scaling.
try adding the cpu freq scaling monitor to your panel and see.

when idle mine runs at 1Ghz

if i do an inf loop with this command (in a terminal):
```
while true;do : ;done

```
it goes to 2.5Ghz
Press ctrl-c to stop the loop.

---

### Post by User3k on 2009-12-21
> **lavinog said:**
> edit: it is because of freq scaling.
try adding the cpu freq scaling monitor to your panel and see.

when idle mine runs at 1Ghz

if i do an inf loop with this command (in a terminal):
```
while true;do : ;done

```
it goes to 2.5Ghz
Press ctrl-c to stop the loop.

With an inf loop in terminal I am getting 2300 MHz each when I run the benchmark. Now is this only to help the benchmark process by maxing out the cpu? And was I wrong thinking that the MHz was split and it is actually 2300 Mhz (or 2200, what ever, lol,) each not total?

---

### Post by lavinog on 2009-12-21
> **User3k said:**
> With an inf loop in terminal I am getting 2300 MHz each when I run the benchmark. Now is this only to help the benchmark process by maxing out the cpu? And was I wrong thinking that the MHz was split and it is actually 2300 Mhz (or 2200, what ever, lol,) each not total?

The inf loop just simulates a demand for cpu cycles...it will not offer any performance gains...it was just to show that the cpu frequency will scale up.

I don't think the clock needs to be split...it just gets shared...picture the cpu as a row boat.  The cores are the ore men, and the clock is the guy who beats the drum to keep the rhythm. 

To conserve energy and minimize heat, the clock speed is reduced when the load is low.
The benchmark you used probably just reads the values from /proc/cpuinfo before loading the cpu.

---

### Post by Yellow Pasque on 2009-12-21
The cores run at the same frequency all of the time.
```
cat /proc/cpuinfo #Should show both cores at idle/1GHz (unless they're loaded with tasks(s))
sudo cpufreq-set -g performance
cat /proc/cpuinfo #Should show both cores at 2.2GHz
sudo cpufreq-set -g ondemand
```

---

### Post by User3k on 2009-12-21
I see what is going on now. Thanks, everyone has been very helpful.

---

