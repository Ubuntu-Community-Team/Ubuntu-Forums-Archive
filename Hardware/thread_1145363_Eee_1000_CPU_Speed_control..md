---
title: "Eee 1000 CPU Speed control."
date: 2009-05-01
forum: Hardware
---

### Post by DecipherXX on 2009-05-01
I got Eee-control for 9.04, and it doesnt appear to work. cat /proc/cpuinfo tells me that the CPU is running at 800MHz regardless of what mode eee-control is in. help?

---

### Post by Giles on 2009-05-03
i had a little search around and found this

> 
If you're just trying to kick up the MHz to see if the throttling is working, open up two terminal windows. In one, run the following:
cat /dev/urandom > /dev/null

In the other, watch the data in /proc/cpuinfo, and it should very quickly show a higher MHz (or bogomips). The other window is hammering the cpu with operations, so make sure to Ctrl+C to kill it when you're done checking the cpuinfo.

crd

i tried this myself and at idle both threads were running at 800 but a few seconds after running
cat /dev/urandom > /dev/null
both threads increased to 1600
hope this helps

---

### Post by fewt on 2009-05-06
> **DecipherXX said:**
> I got Eee-control for 9.04, and it doesnt appear to work. cat /proc/cpuinfo tells me that the CPU is running at 800MHz regardless of what mode eee-control is in. help?

Try EeePC ACPI Utilities, and load the p4_clockmod module.  I know that some people will reply that it's bad and it doesn't work, but I have yet to see any hard evidence that counters output from kill-a-watt and powertop.

[https://sourceforge.net/projects/eeepc-acpi-util](https://sourceforge.net/projects/eeepc-acpi-util)

---

