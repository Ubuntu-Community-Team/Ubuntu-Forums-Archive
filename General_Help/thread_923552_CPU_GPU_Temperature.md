---
title: "CPU GPU Temperature"
date: 2008-09-18
forum: General Help
---

### Post by alejandro.mc on 2008-09-18
I have the following temperatures when doing nothing in my laptop (attached picture). 

CPU   GPU   Core0Temp   Core1Temp

It's only one core, so the two cores have same temperature.

Is this normal?

THX

---

### Post by Titan8990 on 2008-09-18
For a laptop, those temps are fine. Integrated GPUs can usually handle going up to about 85-90C and descrete cards can often handle 100-110.

CPUs are usually getting their "too hot" point at about 60C, depending on the CPU. Some old Pentium 4s and Athlons will actually get even hotter than that.

---

### Post by Steveway on 2008-09-18
Manufactur-wise my Laptop (an Acer) is set to shut down at 80°C.
Right now it is at 50°C and if it runs for a few minutes at full speed it will get to 80 and beyond.
Maybe I'll write a little script that set the CPU to the fastest speed untill it reaches 70°C, then it set's it to the slowest speed untill it is again at about 60°C. Strangely all the CPU-governors that come with cpufreq, powernowd and co are based on CPU-load instead of temperature.
Should we file this as a bug?

---

