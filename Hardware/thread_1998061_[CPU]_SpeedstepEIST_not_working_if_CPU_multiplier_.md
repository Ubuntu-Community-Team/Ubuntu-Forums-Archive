---
title: "[CPU] Speedstep/EIST not working if CPU multiplier manually set in the BIOS"
date: 2012-06-06
forum: Hardware
---

### Post by francois.marot on 2012-06-06
Hi Linuxers !

I currently face a problem with my new computer. I testes it on all versions of K/Ubuntu 12.04, 12.10 64 & 32bits and the new Fedora: it always behaves the same:
if I set a specific max CPU multiplier in the BIOS (in order to overclock), the frequency reduction technology (call it "Speedstep", "EIST" or whatever) does not works on Linux while it works on Windows. In "idle", my CPU should lower its frequency but it does not under Linux (it does when I set the multiplier to "auto" in the BIOS).

My CPU: Core i7 3770K

How do I check ?

** watch grep \"cpu MHz\" /proc/cpuinfo     => displays 3500 MHz for idle and 3501 on load for each core. I've read somewhere that it's normal and 3501Mhz stands for "max". So be it. But the CPU does not seem to lower it frequency to 1600Mhz as it does on Windows... 

** cpufreq-info gives, for each core:
hardware limits: 3.50 GHz - 3.50 GHz
  available frequency steps: 3.50 GHz, 3.50 GHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 3.50 GHz and 3.50 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 3.50 GHz.
  cpufreq stats: 3.50 GHz:0.61%, 3.50 GHz:99.39%  (475)

Between two configurations, one working and the other not working, the only difference is my manual setting of the multiplier in the BIOS.

Anybody got an idea ?

---

### Post by Redblade20XX on 2012-06-07
Hmmm. Maybe this will help point you in the right direction: [https://wiki.archlinux.org/index.php/CPU_Frequency_Scaling](https://wiki.archlinux.org/index.php/CPU_Frequency_Scaling)

I think this might be a software configuration problem.

-Red

---

