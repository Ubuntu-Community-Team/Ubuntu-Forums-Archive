---
title: "CPU Governor: Performance, what power draw and heat consequences are to consider?"
date: 2016-12-29
forum: Hardware
---

### Post by Megadoomer on 2016-12-29
Hi everyone,

while looking for a solution to sound glitches when working on audio with an external sound interface, I learned about the Linux CPU governors. By default, the "ondemand" governor is set for all processors, which enables the system to clock down the CPU in order to save power when idle. The problem when working with digital audio at low latencies is that sometimes, processing spikes can appear, which the governor may not be able to detect fast enough, resulting in crackling and popping noises heard in recording and on the speaker.

One advice that is relatively often found is to manually set the governor to "performance", which forces the CPU to run at the maximum clock speed constantly. I have also tried this solution and it appears to dramatically decrease the amount of interface crashes I receive, meaning I'll have to get used to this setting if I want to work with low latency sound (which I need for software sound monitoring).

I am currently running an AMD FX-8350 processor, so right after setting the governor to the performance-mode, I saw the overall CPU clock rate in the hardware monitor jump from 1-2 GHz straight to 4 GHz, fixed. I assumed that this would automatically also raise temperatures and power consumption dramatically, thereby also increasing fan noise (CPU, maybe also PSU). However, after running the system in this setting for a few hours, I was not able to observe any of this. The CPU stayed relatively cool with just 3-4°C more in heat than before and the CPU cooler was apparently able to maintain the temperature by simply adding 30-40 rpm to the fan, which is completely inaudible to me. This would be something I'm absolutely able to live with for getting better sound performance from my machine.

However, without knowing the exact workings of the governors (reading up proved to be extremely difficult for someone without programming experience) and without being able to measure my computer's actual power consumption at the moment, I'm asking myself the following questions:

1. How much more power does my computer really draw in this state? I saw CPU temperatures still going up under load. Does that mean that the CPU still does not take its full 125W constantly and just when being highly taxed by the system?
2. What kind of difference can I expect concerning power consumption? I read somewhere that AMD's CPUs are not the necessarily the most economic pieces of hardware anyway. What difference could this change make, considering the computer is also used for common low-performance tasks (browsing, listenting to music, writing) a lot? Do I have to start worrying about the planet or is the difference negligible in the end?
3. Does this mode affect any of the CPU's own performance functions? I previously had the AMD "Turbo Core" and "Cool and Quiet" functions enabled. Will they still take effect in some way or should I rather disable them and go for a slight overclock instead?

I would be glad if someone could explain a bit more to me about the correlation between the governor and what I am seeing on my system to make sure this is a viable solution for me or that I have to keep looking.


Kind regards! :)

---

