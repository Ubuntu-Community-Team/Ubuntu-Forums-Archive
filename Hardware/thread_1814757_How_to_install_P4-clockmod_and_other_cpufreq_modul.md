---
title: "How to install P4-clockmod and other cpufreq modules?"
date: 2011-07-30
forum: Hardware
---

### Post by coolbeet on 2011-07-30
Hi everyone, I have a Xserve server with Debian 2.6.26-2-amd64, the cpu is 2 X  Intel Xeon 5150 @ 2.66GHz.

I want to scaling down the cpu frequency and I only found three modules in my system and all of them are not working:

```
lake:/# ls /lib/modules/2.6.26-2-amd64/kernel/arch/x86/kernel/cpu/cpufreq
acpi-cpufreq.ko  powernow-k8.ko  speedstep-centrino.ko
lake:/# modprobe acpi-cpufreq
FATAL: Error inserting acpi_cpufreq (/lib/modules/2.6.26-2-amd64/kernel/arch/x86/kernel/cpu/cpufreq/acpi-cpufreq.ko): No such device
```

I found only module P4-clockmod can work with Xeon processors, but I don't know how to install it into the system.

Any help is greatly appreciated. Thanks.

---

### Post by coolbeet on 2011-08-02
Up~~

---

### Post by tgalati4 on 2011-08-02
You would have to research on how the P4-clockmod module works.  Normally you would just force load it:

sudo modprobe p4-clockmod

There may be some options that are needed on the above command line.

You probably need to set up some configuration files (things that are needed by clockmod and are usually found /proc/acpi).

Xeons are workhorse processors and are not designed to be throttled.  I'm not saying that it won't work, it's just that the architecture of the processor may only support limited throttling capability.  And chances are that the rest of the power bus of the Xserve will still use quite a bit of power, so you may not even see any power savings (a few watts at most).

For instance a Dell PowerEdge 1750 (2 Xeons, 2.8 GHz--4 cores total) burns 240 watts with all for cores at maximum CPU load (burnP6 times four).  But at idle it's 218 watts.  With 7 fans, 3 disks, and a RAID controller, that's a lot of hardware to keep happy.

---

### Post by coolbeet on 2011-08-02
> **tgalati4 said:**
> You would have to research on how the P4-clockmod module works.  Normally you would just force load it:

sudo modprobe p4-clockmod

There may be some options that are needed on the above command line.

You probably need to set up some configuration files (things that are needed by clockmod and are usually found /proc/acpi).



Hi , thank you for the reply.

I tried to force load p4-clockmod but it seems that p4-clockmod isn't exist in my system:

```
lake:/# sudo modprobe p4-clockmod
FATAL: Module p4_clockmod not found.
```

so do I need to recompile the kernel to add p4-clockmod?

Thank you so much~:guitar:

---

