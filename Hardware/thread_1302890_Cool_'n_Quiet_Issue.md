---
title: "Cool 'n Quiet Issue"
date: 2009-10-27
forum: Hardware
---

### Post by jnew93 on 2009-10-27
Hi all! Ok, so here's my problem. I have an AMD Phenom II x2 550 overclocked to 3.4Ghz. Currently I have cool 'n quiet enabled in the BIOS. Now, CNQ operates in steppings, and here is my output data from cpufrequtils:

```
john@Mitsune:~$ cpufreq-info
cpufrequtils 005: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to cpufreq@vger.kernel.org, please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 3.40 GHz
  available frequency steps: 3.40 GHz, 2.40 GHz, 1.90 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 3.10 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 3.40 GHz:0.00%, 2.40 GHz:8.27%, 1.90 GHz:0.62%, 800 MHz:91.11%  (8010)
analyzing CPU 1:
  driver: powernow-k8
  CPUs which need to switch frequency at the same time: 1
  hardware limits: 800 MHz - 3.40 GHz
  available frequency steps: 3.40 GHz, 2.40 GHz, 1.90 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 800 MHz and 3.10 GHz.
                  The governor "ondemand" may decide which speed to use
                  within this range.
  current CPU frequency is 800 MHz.
  cpufreq stats: 3.40 GHz:0.00%, 2.40 GHz:15.50%, 1.90 GHz:2.12%, 800 MHz:82.38%  (19683)

```

Now, the problem lies in that the steppings go 3.40 GHz, 2.40 GHz, 1.90 GHz, 800 MHz BUT the cap on speed is 3.10 GHz. This means the processor will never go beyond the 2.4Ghz stepping as you can see.

Can anyone tell me how to override the preset policy on speed steppings to allow the overclocked range to be open? Thanks in advance!

---

