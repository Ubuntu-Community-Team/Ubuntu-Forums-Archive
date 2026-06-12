---
title: "cpufreqd not starting through /etc/rc*.d"
date: 2005-03-30
forum: Hardware &amp; Laptops
---

### Post by ikletti on 2005-03-30
Hi.

I have a Compal CL-50 laptop with a 1.4 GHz Pentium M and I am running Wharty with the standard kernel.
The CPU frequency scaling worked fine, without cpufreqd installed, but it scaled whether the machine
was on AC or battery power.
So I installed cpufreqd and tweaked the configuration file so that the CPU stays at 600 MHz when running
on battery power and scales between 800 MHz - 1400 MHz when running on AC.

The only issue that I have right now is that cpufreqd does not start on boot. I did add it to the startup scripts
with "sudo rc-update.d cpufreqd" (I've checked and the link does exist in the /etc/rc*.d directories), but it does
not load on boot. I still have to open a terminal and do "sudo /etc/init.d/cpufreqd start" to get it up and running.

Is there something that I am missing?

Ingo.

---

### Post by rusi_pathan on 2005-03-30
Doesnt powernowd takes care of the scaling ?

---

### Post by ikletti on 2005-03-30
> Doesnt powernowd takes care of the scaling ? 
No. I don´t have powernowd installed, though that would be possible.

Cpufreqd and powernowd essentially do the same task: They scale the CPU
frequency according to the required computing power (which is derived from
the CPU duty cycle).
I have decided to use cpufreqd, though many people might find it hard to
configure. All I can say is that it works pretty well for me. The only annoyance
is that it currently is not loaded correctly during the boot process.

Ingo.

---

