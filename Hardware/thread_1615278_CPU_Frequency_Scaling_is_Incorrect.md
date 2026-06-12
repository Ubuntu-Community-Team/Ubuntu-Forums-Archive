---
title: "CPU Frequency Scaling is Incorrect"
date: 2010-11-06
forum: Hardware
---

### Post by jnew93 on 2010-11-06
Hello all, I'm currently running 10.10 64 Bit Desktop Edition. I have an AMD Phenom IIx2 550, Stock clocks 3.1Ghz, but overclocked and overvolted to 3.6Ghz at 1.46v. I would prefer to use AMD's Cool and Quiet CPU scaling, and in windows it works just fine, that is, when I overclock the multiplier in the BIOS (I don't overclock the FSB), windows will correctly adjust the frequency scaling.

In Ubuntu, this is not the case. At stock frequencies, the scaling is such:

800Mhz
1900Mhz
2400Mhz
3100Mhz

And under linux this works wonderfully with the ondemand governor. The problem arises when I overclock and boot to linux. Using cat /proc/cpuinfo, I can see that the scaling is now:

800Mhz
1900Mhz
2400Mhz
3600Mhz

This does not work, the CPU is never running at more than 2400Mhz, even with Prime95 going. I just can't seem to get it to scale up to 3600! Now, my question to all you is: how can I fix the scaling without having to turn it off in BIOS all together? Thanks in advance!

---

### Post by jnew93 on 2010-11-07
Well, I've figured out that by disabling cool and quiet from BIOS, the processor will run at a constant 3600Mhz in ubuntu. Sucks though, because I really want scaling, and cpufreq fails on boot now.

Nobody has the knowledge to lend a hand? If I'm better off asking this in a different place, please let me know and I will.

---

### Post by v1ad on 2010-11-07
.. i did some work with this but already forgot what i did.. 

reinstall cpufreq and open synaptic manager and search cpu . u can get a few cpu utilities there. if i'll find something i'll let u know.

---

