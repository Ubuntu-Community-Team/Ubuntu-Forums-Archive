---
title: "CPU electrical power monitoring?"
date: 2012-08-06
forum: Hardware
---

### Post by Ranko Kohime on 2012-08-06
[Core Temp]("http://www.alcpu.com/CoreTemp/"), which as far as I know is a Windows-only program, but there is a feature within that program that I'm wondering if it's taken advantage of by any program on Linux, specifically it gives a reading of the processor's electrical power consumption in Watts.

If it's reported anywhere in /proc, that would work well enough.  I looked, but didn't find anything obvious.

My Processor is an i3-2310M, (Sandy Bridge).

---

### Post by ajgreeny on 2012-08-06
I am not sure if this will do what you want, but have a look at **powertop**, a command line application run with the command "sudo powertop," which will tell you the total watts used by a laptop when on battery, and allows you to tune hardware for better battery use.  I am not certain whether it does the same when on mains supply, or therefore, when used on desktop machines.

---

### Post by Ranko Kohime on 2012-08-07
I have used Powertop, but it does not—to my knowledge—give any reading on the CPU, just what threads are waking it up, under the logical assumption that if the CPU is awoken then it's using power.

---

