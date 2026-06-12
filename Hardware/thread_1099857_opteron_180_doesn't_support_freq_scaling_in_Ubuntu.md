---
title: "opteron 180 doesn't support freq scaling in Ubuntu??"
date: 2009-03-18
forum: Hardware
---

### Post by opto-laptop on 2009-03-18
Hi,

I know there are other similar threads like this on here, but I haven't found an answer.
Other threads I read are along the lines of "frequency scaling not working". Well I've got a problem one step more frustrating. 

I've installed Mint 6 x64 and is running the 2.6.27.17-generic kernel and while the logs and utilities all report the CPU family and name correctly, they say Scaling is not supported.
The /sys/devices/system/cpu/cpu0/cpufreq directory doesn't even exist under cpu0 or cpu1.

It reports the cpus running at 1ghz instead of 2.4 that it should be. As other people say in their threads, this worked fine under windows xp and tools like cpu-z report all the correct information and speeds of both CPU and RAM. Cool n Quiet works in Windows (but I set it to run full speed always via RMclock). So this should detect as a 2.4Ghz capable cpu in Linux too.

I've tried rebuilding a kernel as AMD focused but it doesn't seem to help. I've tried the server version of ubuntu kernel and that didn't change anything either (except for the Nvidia drivers won't load with that but that's a tale for a different thread).

Does anyone have any other ideas?

Cheers,
Damian

---

