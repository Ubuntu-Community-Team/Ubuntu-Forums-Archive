---
title: "Powernowd and only two frequency steps"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by flapane on 2007-01-04
I installed dapper i386 on an athlon xp mobile 2ghz and abit nf7 2.0, and powernowd, as confirmed by cpufrq-info, has only 2000mhz and 1500mhz steps. How to scale the frequency at 800mhz or 1000mhz in idle ?

---

### Post by lcaley on 2007-01-04
I'm by no means an expert on this, but this is similar to my thread I just posted, so I thought I'd pass on the knowledge I've gained in the last few days working on my cpu frequency. 

try the command:
sudo cpufreq-set -g conservative

that supposed to set your cpu to the conservative governor, which will keep your cpu at the minimum until you need more power, and it steps it up little by little according to what it needs. But, assuming that it works, your in the same boat as me, the governor will default to what it is currently when you reboot, and I don't know how to not make it do that.


Hope this helps.

---

### Post by flapane on 2007-01-05
yes but the problem is that cpufreq says that the hardware limits are only 1500-2000, so it couldn't never go lower than 1500mhz, and this is very strange

---

### Post by RandomJoe on 2007-01-05
I believe that's just what the hardware can do.  I have older P4 systems that use the P4-clockmod governor which do as you describe - 300MHz steps from 600MHz all the way to 2.4GHz.  But every new system I've seen only has the two steps.  My understanding from asking about it way back when is that the new systems are adjusting the CPU voltage on that step as well, and that's where the big power savings comes in, not the frequency scaling.

I have a Dell laptop with a P4 mobile processor which lets me use either the P4-clockmod governor (which gives me all the steps) or the speedstep governor (only two steps) and the system runs considerably cooler with the speedstep governor, even though it only drops to 1GHz as opposed to 300-400MHz with the clockmod one.

---

### Post by flapane on 2007-01-06
In windows xp, using 8rdavcore, I used the 1330mhz and 2000ghz steps setting them by hand, I don't know why now it choose the 1500mhz step.
ANyway the temperature is good, lower than 38°C

---

