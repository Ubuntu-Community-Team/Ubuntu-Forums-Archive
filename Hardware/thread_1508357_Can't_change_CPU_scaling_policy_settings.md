---
title: "Can't change CPU scaling policy settings"
date: 2010-06-12
forum: Hardware
---

### Post by ferossan on 2010-06-12
Hi all

I'm trying to set my CPU scale "ondemand" from the minimum to the maximum of my CPU scaling capacity. It is supposed to be from 800 MHz to 2.10 GHz
I'm using cpufreq-set but it does not work (see below).
I'm running Lucid and my hardware is a Lenovo T61 with a Intel Core 2 Duo CPU T8100 @ 2.10GHz
BIOS setting is set both Battery and AC to "Performance"

Here is my cpufreq-info output:
====================
$ [COLOR="Blue"]cpufreq-info
cpufrequtils 006: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.10 GHz
  available frequency steps: 2.10 GHz, 2.10 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  **current policy: frequency should be within 800 MHz and 1.20 GHz.**
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 1.20 GHz.
  cpufreq stats: 2.10 GHz:0.00%, 2.10 GHz:0.00%, 1.60 GHz:0.00%, 1.20 GHz:68.02%, 800 MHz:31.98%  (1427)
analyzing CPU 1:
  driver: acpi-cpufreq
  CPUs which run at the same hardware frequency: 0 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 10.0 us.
  hardware limits: 800 MHz - 2.10 GHz
  available frequency steps: 2.10 GHz, 2.10 GHz, 1.60 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  **current policy: frequency should be within 800 MHz and 1.20 GHz.**
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 2.10 GHz:0.00%, 2.10 GHz:0.00%, 1.60 GHz:0.00%, 1.20 GHz:5.06%, 800 MHz:94.94%  (2939)[/COLOR]

====================
Trying the following for the Core 0:
$ [COLOR="Blue"]sudo cpufreq-set -c 0 -u 2100000[/COLOR]
Does not work.
But trying:
$ [COLOR="Blue"]sudo cpufreq-set -c 0 -u 1200000[/COLOR]
It does.

Why can't I set it to 2.10 GHz as the maximum?
How can I change the policy be within 800 MHz and 1.20 GHz to 800 MHz and 2.10 GHz?

Thanks.

---

### Post by cbowman57 on 2010-06-13
I use powernowd, it also gives you an applet (governor plugin) to adjust ondemand, performance etc.  I just use the cpu_freq applet to show me that it's working.

Seems to work ok in meerkat too.

---

### Post by ferossan on 2010-06-13
> **cbowman57 said:**
> I use powernowd, it also gives you an applet (governor plugin) to adjust ondemand, performance etc.  I just use the cpu_freq applet to show me that it's working.

Seems to work ok in meerkat too.

Do you mean the governor plugin for the Xfce4 panel?
Any way, I tried powernowd command line and it shows the 5 "steps" that my CPU is capable, but it does not rise to 2.1 GHz despite any load. Only rise to 1.2 GHz
$ sudo powernowd -u 100
powernowd: PowerNow Daemon v1.00, (c) 2003-2008 John Clemens
powernowd: Found 2 scalable units:  -- 1 'CPU' per scalable unit
powernowd:   cpu0: 800Mhz - 2101Mhz (5 steps)
powernowd:   cpu1: 800Mhz - 2101Mhz (5 steps)

I'm under Gnome monitoring with the "CPU Frequency Scaling Monitor" panle applet.

---

### Post by ferossan on 2010-06-18
Well, after several tries, no luck yet.
Apparently, for some reason, my current Lucid install is reading the BIOS limited to 1.20 GHz and not to the maximum possible (2.10 GHz)
I can say that because the file:
/sys/devices/system/cpu/cpu0/cpufreq/bios_limit
says: 1200000 and I can't find any way to change it to 2101000.

My first thinking was a BIOS setting problem. To test it, -without- change the BIOS, I did run my Ubuntu Live CD (Lucid) and I was able to scale my Laptop to 2.10 GHz without problem.

So, I'm out of ideas now.

Apparently, the /sys/devices/system/cpu/ files are generated at boot, that is why I can't edit them, but for some reason, the bios_limit file is wrong generated and it is -not- a BIOS setting problem (Ubuntu Live CD recognize fine the upper limit).

Does anyone have an idea what is going on here?

---

### Post by endlesstars on 2010-08-01
bump
i'm interested in this too since i'm trying to get an higher multiplier for my asus u30vt and i can't do it from bios. it seems that all the files in the cpus folder can0t be written, in contrast to what it says here ([http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=Documentation/cpu-freq/user-guide.txt;h=917918f84fc75ac09061be1f1f242159823983cf;hb=HEAD](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=blob;f=Documentation/cpu-freq/user-guide.txt;h=917918f84fc75ac09061be1f1f242159823983cf;hb=HEAD)). anyone with a deeper understanding of the internals of ubuntu power management can shed some light?

---

### Post by conradin on 2010-08-01
Ive found this link helpful for my scaling needs.
[http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/](http://embraceubuntu.com/2005/11/04/enabling-cpu-frequency-scaling/)

---

### Post by endlesstars on 2010-08-01
this seems to be fixed in later ubuntus because my lucid permits me to change multiplier from the applet without haveing cpufreq-selector set as setuid (i don't know how). the problem tho is that the frequencies desired don't even show up, and the policies can't be changed to "OverClock" the cpus back to where they should be.

---

### Post by ferossan on 2010-08-01
> **endlesstars said:**
> this seems to be fixed in later ubuntus because my lucid permits me to change multiplier from the applet without haveing cpufreq-selector set as setuid (i don't know how). the problem tho is that the frequencies desired don't even show up, and the policies can't be changed to "OverClock" the cpus back to where they should be.

Yeah, in Lucid seems to be working with stock Kernel and updates, but not others like those from [http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/).
In my particular case, using -non stock Kernels- on a Lenovo Thinkpad T61 (others could be affected too), was impossible to change the CPU scaling policy **on AC power _without_ battery**, in fact, was my objective. It is also reported here:
[http://www.thinkwiki.org/wiki/Problem_with_CPU_frequency_scaling](http://www.thinkwiki.org/wiki/Problem_with_CPU_frequency_scaling)

---

### Post by goldenshale on 2011-02-07
I'm having this problem also, in Meerkat.  My Dell Latitude D630 normally does 2.6 GHz, but now the policy is set to have a max and min of 800 MHz.  I've tried changing with the applet and the cpufreq-set util with no luck.

---

### Post by ferossan on 2011-02-07
> **goldenshale said:**
> I'm having this problem also, in Meerkat.  My Dell Latitude D630 normally does 2.6 GHz, but now the policy is set to have a max and min of 800 MHz.  I've tried changing with the applet and the cpufreq-set util with no luck.

Perhaps the AC adaptor does not supply enough power to handle peak power draws from the CPU. The battery is required to supply the peak demand and ensure correct system operation
Are you using the battery set in? That solved my problem.

---

