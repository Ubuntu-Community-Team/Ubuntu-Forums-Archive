---
title: "Upgrading from 32bit / 64bit?"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by xdemo on 2009-10-09
Hello everyone ;p

Basically i want to be able to know if i can upgrade from 32bit Jaunty, to 64bit Karmic (when the final is released in 20days time)

Is this possible? I have recently found out my Computer is 64bit compatible... But for some reason, when i bought this PC it came with 32bit Windows Vista pre-installed, seems kind of odd.

```
       product: AMD Athlon(tm) 64 X2 Dual Core Processor 5000+
       vendor: Advanced Micro Devices [AMD]
       physical id: 6
       bus info: cpu@0
       version: 15.11.2
       size: 2600MHz
       capacity: 2600MHz
       width: 64 bits

```

I have heard about a few proprietary software being unstable on 64bit Ubuntu, however its not really an issue for me.

Pretty sure im using 32bit atm...
```
demo@jaunty:~$ uname -m
i686

```

So how do i change/upgrade from a 32bit install to a 64bit install, or if not, would i have to completely re-partition/install from scratch?

Thank you in advance.

---

### Post by tommcd on 2009-10-09
You can verify that your CPU is 64 bit by running:
```
cat /proc/cpuinfo
```
In the **flags** line in the output look for **lm**. If lm is there then the CPU is 64 bit.
I don't believe there is any reliable way to upgrade from 32 bit to 64 bit without a reinstall of 64 bit Ubuntu.

---

### Post by xdemo on 2009-10-09
Yes, there is the lm flag. Ah i guess i need to re-burn another CD. 

Thank you for your response.

---

