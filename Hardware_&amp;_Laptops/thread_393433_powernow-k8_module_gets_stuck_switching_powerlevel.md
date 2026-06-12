---
title: "powernow-k8 module gets stuck switching powerlevels on dualcore AMD64."
date: 2007-03-25
forum: Hardware &amp; Laptops
---

### Post by noris2go on 2007-03-25
Hi,

I am having this annoying problem and any help would be appreciated. 
My powernow-k8 module gets stuck switching powerlevels on dualcore AMD64.

I am running Ubuntu 6.10 Edgy (AMD64) on a ASUS A8V-MX with a dual core Athlon64.

I am loading the powernow-k8 module and the governors (cpufreq_ondemand, cpufreq_conservative) using "/etc/modules".

I have tried three kernels (2.6.17-10-generic, 2.6.17-11-generic, 2.6.20-12-generic)
and on all of them I am getting this error after which the power management gets stuck and does not work anymore.

[  454.266700] powernow-k8: Hardware error - pending bit very stuck - no further pstate changes possible
[  454.266709] powernow-k8: transition frequency failed
[  455.504471] powernow-k8: failing targ, change pending bit set

It usually happens when switching back from a high power state to a low power.
I am using these CPU intensive commands to ramp up each core to 100%:

ssh-keygen -G moduli.1 -b 1024 &
ssh-keygen -G moduli.2 -b 1024 &

Is this a bug I may hope to get fixed or am I doing something wrong ?
Thank you.

---

