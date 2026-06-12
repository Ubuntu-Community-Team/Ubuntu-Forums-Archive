---
title: "cpufreq scaling to lowest setting when processor usage is high"
date: 2009-09-11
forum: Hardware
---

### Post by agrteknolan on 2009-09-11
I've been doing some media trans-coding at work over the past week and when both cores are above 65% usage it places the cpufreq scaling at the lowest setting.

I'm using Ubuntu 9.04 x64 on a system76 pangolin performance laptop.

Can I provide more information that will help diagnose this?

Am I just bad at searching and has this been solved?

---

### Post by Fafler on 2009-09-11
I experience something similar, although i haven't looked that much into it.
Install CPU Frequency Scaling Monitor and add it to you gnome panel. Then just select performance from the dropdown menu. And go back to ondemand or powersace when you're done.

---

### Post by agrteknolan on 2009-09-11
> **Fafler said:**
> I experience something similar, although i haven't looked that much into it.
Install CPU Frequency Scaling Monitor and add it to you gnome panel. Then just select performance from the dropdown menu. And go back to ondemand or powersace when you're done.

Good advice, but it doesn't work, a few moments in to the jobs and it flips back the 1.2Ghz and I can't change it until cpu usage goes down.

---

### Post by agrteknolan on 2009-09-11
It appears do be a heat issue, once I get above 70c is when it clicks over. I'll hit up the system76 guys for more info.

---

### Post by agrteknolan on 2009-09-11
> **agrteknolan said:**
> It appears do be a heat issue, once I get above 70c is when it clicks over. I'll hit up the system76 guys for more info.

Nevermind, I'm sitting at 81.8 and at full speed . . . bizzare

---

### Post by recluce on 2009-09-11
> **agrteknolan said:**
> Nevermind, I'm sitting at 81.8 and at full speed . . . bizzare

If you have a multi-core machine: are you monitoring **all** core temperatures? If your application runs on one core only, temperatures can get quite uneven between the cores. Not typical, but it does happen.

Otherwise, your system seems to behave correctly for a high-temperature scenario...

---

### Post by agrteknolan on 2009-09-11
> **recluce said:**
> If you have a multi-core machine: are you monitoring **all** core temperatures? If your application runs on one core only, temperatures can get quite uneven between the cores. Not typical, but it does happen.

Otherwise, your system seems to behave correctly for a high-temperature scenario...

I'll have to try it a few times, but providing airflow seems to help (I only have the one temp sensor apparently, so I can't accurately gauge both cores).

---

