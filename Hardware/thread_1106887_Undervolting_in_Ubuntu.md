---
title: "Undervolting in Ubuntu?"
date: 2009-03-26
forum: Hardware
---

### Post by sol_kanar on 2009-03-26
Hi! I have an Ubuntu machine (but I am still quite a n00b), and I need to lower cpu voltage for a project I am working on: I have to do that via software, because I need to try different voltage values.

Is there a way to set cpu voltage in Ubuntu? I know of a few programs, but they only run on Windows (e.g. CrystalCPUid); cpufreqd will not let me set voltage (frequency only); and I did not understand exactly if phctool is usable/updated in Ubuntu.

Thank you for your help :-)

---

### Post by sol_kanar on 2009-04-20
Hi!

I managed to reduce cpu VID via Intel Enhanced Speedstep control. Basically, now I can read and write values into the MSRs (Machine-Specific Registers) of the desktop I'm working on: some of these MSRs store information about voltage and frequency.

I tried to write values into the MSR that controls the Speedstep and I managed to lower cpu VID to 1.350V to 1.238V: the problem is, it looks like that some process is working against my settings, because when the CPU is heavily loaded (e.g. by some stress test like mprime - Mersenne Prime) cpu VID comes back to its maximum value (1.350V).

I removed all the daemons that I believe can influence voltage and Speedstep (cpufreqd, kacpi, powernowd, powertweak), but nothing works: each time the CPU is loaded, cpu VID switches back to 1.350V .

Can anyone help me? Did I forget some process that could be working against me? (I am running an Ubuntu 8.10 distribution)

Thank you for your time :-)

---

