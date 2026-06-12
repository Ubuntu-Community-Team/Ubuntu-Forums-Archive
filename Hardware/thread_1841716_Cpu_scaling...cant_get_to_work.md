---
title: "Cpu scaling...cant get to work"
date: 2011-09-09
forum: Hardware
---

### Post by Whoop365 on 2011-09-09
ok well I'v spent over an hour trying to get this to work, i have an HP Dv7...that loves to over heat, easily gets up to 75C/160F after short term use...

well heres what happens when i type cpufrew-info


whoop365@whoop365:~$ cpufreq-info
cpufrequtils 007: cpufreq-info (C) Dominik Brodowski 2004-2009
Report errors and bugs to [email]cpufreq@vger.kernel.org[/email], please.
analyzing CPU 0:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 0
  CPUs which need to have their frequency coordinated by software: 0
  maximum transition latency: 8.0 us.
  hardware limits: 800 MHz - 2.30 GHz
  available frequency steps: 2.30 GHz, 2.10 GHz, 1.50 GHz, 1.10 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 2.30 GHz and 2.30 GHz.
                  The governor "conservative" may decide which speed to use
                  within this range.
  current CPU frequency is 2.30 GHz.
  cpufreq stats: 2.30 GHz:99.06%, 2.10 GHz:0.93%, 1.50 GHz:0.00%, 1.10 GHz:0.00%, 800 MHz:0.01%  (18)
analyzing CPU 1:
  driver: powernow-k8
  CPUs which run at the same hardware frequency: 1
  CPUs which need to have their frequency coordinated by software: 1
  maximum transition latency: 8.0 us.
  hardware limits: 800 MHz - 2.30 GHz
  available frequency steps: 2.30 GHz, 2.10 GHz, 1.50 GHz, 1.10 GHz, 800 MHz
  available cpufreq governors: conservative, ondemand, userspace, powersave, performance
  current policy: frequency should be within 2.30 GHz and 2.30 GHz.
                  The governor "performance" may decide which speed to use
                  within this range.
  current CPU frequency is 2.30 GHz.
  cpufreq stats: 2.30 GHz:99.06%, 2.10 GHz:0.93%, 1.50 GHz:0.00%, 1.10 GHz:0.00%, 800 MHz:0.01%  (16)













Now some of that seems to make since to me, but the current policy part sais i can only choose 2.3 - 2.3

I'm not exactly sure what to do...Any ideas? help? Thank you

---

### Post by 2F4U on 2011-09-10
I would suggest that you switch to the ondemand governor. The conservative governor you are currently using is just what it is named, it is conservative in that it only rarely adjusts CPU frequencies.

---

### Post by edgar83 on 2011-09-12
I've got exactly the same problem (IBM MICROSERVER here).

It looks that min and max frequencies have the same value and I can't change them (I've tried with cpufreq-set -d xxx -u xxx -g ondemand and nothing changes...) :confused:

---

### Post by .... on 2011-09-12
It looks like you're only changing the governor of one core, as the second one is still on "performance" (my Athlon II lappy has the same issue with some distros).

---

### Post by vanquishedangel on 2011-09-29
Not to jack a thread but this maybe related, I have a hp dc7100 with a intel p4 3.8 ghz ht and it will only use performance governor, I want to use ondemand and learned that with the p4_clockmod the latency inter fears with scaling. as for your issue I had that problem, it is a setting somewhere but I been working at this for so long I cant remember, try editing cpufrequtls in /etc/init.d and set the values.

if anyone can help with the latency so that I may use ondemand cool.

---

### Post by diasf on 2011-09-29
cpufreqd.conf
Check the documentation and do you own version of the file. Might be confusing at the start, but at the end you can do whatever you want/need with it.

---

### Post by jerm1027 on 2012-01-01
I know GNOME has an applet that allows you to manually set the CPU frequency or governors. I use it on my gaming laptop equipped with a power hogging Core 2 Duo T9600 at 2.8GHz running Linux Mint 11 (Uses Gnome 2). I add as many applets as I have cores to my top panel, and configure each applet to report a specific core. This way I can see all my cores and set the frequency/governor on individual cores. When I'm battery, I always set both cores to 800MHz. However, since power isn't much of an issue on my desktop, I stopped using it on my quad-core desktops.

I've been looking all over for a similar program or applet for different desktop environments (LXDE, and XFCE mainly), but I've been unsuccessful in my search. I would really love to having it with Lubuntu on my AMD C-60, because I know word processing doesn't take a dual-core 1GHz CPU.

As for the main version of Ubuntu, I just gave up on it. Unity bugs me, and I can't really configure anything without opening the terminal and inputting 50 different commands, or installing additional software. it seems to be drastically different from the distros based on it, official or otherwise. So, I'm not sure how to help here.

---

