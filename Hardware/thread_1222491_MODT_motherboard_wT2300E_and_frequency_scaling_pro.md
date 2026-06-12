---
title: "MODT motherboard w/T2300E and frequency scaling probs"
date: 2009-07-24
forum: Hardware
---

### Post by liquidonline on 2009-07-24
Hi all,

I've been looking to find a quiter/cheaper alternative to my quadcore that I can leave on all day.  I ran into a deal for an abit il-90V with a T2300E core duo.  This is perfect for my needs except for one thing... it seems ubuntu doesn't "see" the CPU right.

lshw correctly states the cpu is a T2300 1.6ghz cpu.  However the output of /proc/cpuinfo, and /proc/acpi/processor/CPU?/* does not jive.  It says unsupported for most stuff, but the intriguing thing is that it says the max speed is 1ghz.  The bios also correctly shows it as 1.6ghz.

sandro@achilles:~$ cat /proc/acpi/processor/CPU0/info
processor id:            0
acpi id:                 0
bus mastering control:   no
power management:        no
throttling control:      no
limit interface:         no

sandro@achilles:~$ cat /proc/acpi/processor/CPU0/limit
<not supported>

sandro@achilles:~$ cat /proc/acpi/processor/CPU0/power
active state:            C0
max_cstate:              C8
bus master activity:     00000000
maximum allowed latency: 2000000000 usec
states:

sandro@achilles:~$ cat /proc/acpi/processor/CPU0/throttling 
<not supported>

The above were done after trying everything possible to put the state to "performance"

I've used ubuntu on many laptops and I ran dpkg-reconfigure gnome-applets as well as installing powernowd (which I previously never required) to no avail.

Is there any way to know what the CPU is "actually" running at?  Granted it's painfully unscientific, but I turned off speedstep/enhanced C states and it still said 1ghz, which I figure is impossible.  Also, (again unscientific) based on the temps alone, i'm certain that it's currently running at full speed.

---

### Post by liquidonline on 2009-07-25
Well,

I tried going with OpenBSD because I'm much more familiar with the BSD's, and the sysctl for cpuspeed, when I set hw.setperf to 100 is still 1000mhz.  Again, same was true even when I set the speedstep off in the bios.

I'm about to waste an ms action pack liscence to install windows on this just to see if it's a linux/unix compatibility issue or something worse.

Again, if anyone has any thoughts they can chime in with, it would be greatly appreciated.

---

