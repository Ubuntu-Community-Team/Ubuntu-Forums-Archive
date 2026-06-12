---
title: "CPU temperature spikes in dmesg output but not shown in Psensor plot"
date: 2019-02-01
forum: Hardware
---

### Post by Wonder_Full on 2019-02-01
I am running Ubuntu 18.04LTS on Dell Latitude X7480, with intel CPU Core(TM)  i7-7600U. From time to time, if I check the dmesg output, I will see a spike in CPU temperature for a very short instant (far shorter than 1 sec), like this 

[94967.359953] CPU0: Core temperature above threshold, cpu clock throttled (total events = 75)
[94967.359954] CPU2: Core temperature above threshold, cpu clock throttled (total events = 75)
[94967.359955] CPU1: Package temperature above threshold, cpu clock throttled (total events = 589)
[94967.359956] CPU3: Package temperature above threshold, cpu clock throttled (total events = 589)
[94967.359958] CPU2: Package temperature above threshold, cpu clock throttled (total events = 589)
[94967.359961] CPU0: Package temperature above threshold, cpu clock throttled (total events = 589)
[94967.360936] CPU0: Core temperature/speed normal
[94967.360936] CPU2: Core temperature/speed normal
[94967.360937] CPU0: Package temperature/speed normal
[94967.360938] CPU2: Package temperature/speed normal
[94967.360968] CPU3: Package temperature/speed normal
[94967.360968] CPU1: Package temperature/speed normal

This message shows that the temperature returned to normal within 1 msec.  Such a short time cannot be detected in temperature monitoring softwares such as psensor. The output of psensor shows the CPU temperature has been well in the normal range. Another thing is that this kind of temperature spike occurs when the system is idling as well. If I do not check the dmesg output, I won't notice any CPU throttling. In fact, I haven't, since the throttling time is too short to notice. However, something must have gone wrong, either with the hardware or the software.

Since I first noticed this issue in Feb 2018, I have changed a few motherboard (there were other issues as well). I had always blamed the hardware, e.g, the mother board, for this. Now I am running on a completely new motherboard and all other issues are gone, yet, I still see the spikes in CPU temperature in dmesg. 

Anyone got any idea? Thanks.

---

### Post by TheFu on 2019-02-02
Intel CPUs have internal thermal protections. Likely have a cooling issue with the CPU.  The CPU is triggering the alert.

Check that there isn't any dust, the fan can spin as necessary and thermal grease is correctly applied to the heat sink.  I had the same issue with a Core i7-920 (1st gen). It ran that way for the last year doing 4+ hrs of video transcoding most days. Only 2 of the cores had the heating issue and slowed on my system.

---

### Post by CatKiller on 2019-02-02
> **Wonder_Full said:**
> However, something must have gone wrong, either with the hardware or the software.

All sensor signals are noisy. Nothing's actually happening.

---

