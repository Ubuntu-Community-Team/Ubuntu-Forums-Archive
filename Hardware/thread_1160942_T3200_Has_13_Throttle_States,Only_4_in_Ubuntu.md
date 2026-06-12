---
title: "T3200 Has 13 Throttle States,Only 4 in Ubuntu"
date: 2009-05-16
forum: Hardware
---

### Post by starfly on 2009-05-16
Hello,

Ive got a little Powersave Problem...2 days ago ive beginned to play a little with PHC to save power... Ive compiled my kernel, phc didnt work, but OH WONDER, ive got throttles from 250mhz ti 2ghz...

Problem : I dont know what to edit in the menuconfig via compiling, to to it again on an other kernelversion...Here ive got only 4 States again, can someone help me to get 13 Stages again.

Or tell me what COnfig in Menuconfig is to change to activate it again, becaus so my system runs minimum on 1GHz, 250Mhz is what the Cpu can do...

And it worked, until ive set the system new up, and now after 4th compile, theres still no 13 Stages anymore... :-(

In Kernel 2.6.28 it was :

P-Drivers (M)
Opteron (Deactivate)
Enhaced Speedstep (Deactivate)
p4-clockemulation (Deactivate)

( All without any patching, it works, build, restart, 13 Stages)
But in 2.6.30 there are More Options and my 13 Stages dont come on after Compiling from source...only 4 like e ver before... :(

Hope Someone could help me...

---

### Post by starfly on 2009-05-17
bump

---

### Post by PatrickVogeli on 2009-05-17
There's nothing wrong there I believe. Throttling states and scaling states are two different things, so what you're getting is just fine.

You could try to build the P-states driver AND the Pentium 4 Clockmodulation both as modules, then unloading the acpi-cpufreq and then loading the p4-clockmod one, to see what happens. But.. then you'll lose phc. As said... it's different things, so don't worry, it's fine with what you get.

Probably, the time you got so many states was because you compiled the p4-clockmod driver instead of the acpi-cpufreq one.

---

