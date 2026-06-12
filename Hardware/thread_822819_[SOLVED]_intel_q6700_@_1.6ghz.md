---
title: "[SOLVED] intel q6700 @ 1.6ghz??"
date: 2008-06-08
forum: Hardware
---

### Post by ipburbank on 2008-06-08
hey, I just ran geekbench to benchmark my system, and it said that i was running at 1.6ghz on my new intel q6700 quad core that is supposed to run @ 2.6 ghz!!:confused: Any idea why?

---

### Post by thideras on 2008-06-08
It is because the power saving features "Speedstepping" (also labeled as EIST) and "C1E" are enabled in the BIOS.  Under load, the processor will *instantly* jump back up to 2.6GHz.  If you want it to run 2.6GHz all the time, disable those features listed above.

---

### Post by ipburbank on 2008-06-17
> **thideras said:**
> It is because the power saving features "Speedstepping" (also labeled as EIST) and "C1E" are enabled in the BIOS.  Under load, the processor will *instantly* jump back up to 2.6GHz.  If you want it to run 2.6GHz all the time, disable those features listed above.

thank you very much, i changed that and will check the benchmarks when I get home, but the other thing I noticed is that ubuntu's CPU scaling Monitor is going between 1.6 and 2.6 when the CPU is pinned (rendering if it makes a difference). :confused:

---

### Post by stchman on 2008-06-17
> **ipburbank said:**
> hey, I just ran geekbench to benchmark my system, and it said that i was running at 1.6ghz on my new intel q6700 quad core that is supposed to run @ 2.6 ghz!!:confused: Any idea why?

Yes, my Q6600 Core 2 Quad runs at 1.6GHz idle and jumps to 2.4 when needed.  

I also am wondering, I have overclocked my 2.4GHz to 3.0GHz and Ubuntu still reports the processor as 2.4GHz.  I am guessing that Ubuntu is simply reading the processor ID and not actual frequency at all.  How to I get accurate report of the CPU freq?

---

### Post by ipburbank on 2008-06-18
so, um, ya... I turned off c1e and EIST, but my CPU frequency scaling monitor is still showing the CPU as not being at full function most of the time, even when the CPU is pinned it jumps between 3.5 and 2.10. Did i do it wrong? incase it matters i have an abit IP35Pro...

---

### Post by thideras on 2008-06-19
> **ipburbank said:**
> so, um, ya... I turned off c1e and EIST, but my CPU frequency scaling monitor is still showing the CPU as not being at full function most of the time, even when the CPU is pinned it jumps between 3.5 and 2.10. Did i do it wrong? incase it matters i have an abit IP35Pro...Go to System<Administration<Services (in gnome) and disable "CPU Frequency manager".

---

### Post by ipburbank on 2008-06-20
> **thideras said:**
> Go to System<Administration<Services (in gnome) and disable "CPU Frequency manager".

that was it! thank you very much.:popcorn:

---

