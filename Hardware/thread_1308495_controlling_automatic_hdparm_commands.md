---
title: "controlling automatic hdparm commands"
date: 2009-10-31
forum: Hardware
---

### Post by AMAMH on 2009-10-31
when I was using the **beta** 9.10, there was a script in /etc/acpi/start.d/ called somthing like:
90-hdparm*
it was executed on startup, it does "hdparm -B 254 /dev/sda" when on AC power or -B 128 when on battery.

after installing the **final** 9.10, that script doesn't exist anymore but I think the "hdparm" commands are still executed on startup because I found no clicks (no Load_Cycle_Count increments) + very high temp on AC and very rapid clicks + low temp on battery that's exactaly what happened in beta because of hdparm -B 254 and hdparm -B 128 correspondingly.


my question is:
If there is no script, how can I customize/remove that feature, I want to be able to control it, or maybe I'm wrong and the system doesn't execute hdparm commands on startup (I don't think I'm wrong)?
pls guys, I don't wanna have chat here, if u got the answer/something useful say it.
sry, if I sound arrogant :p

---

### Post by AMAMH on 2009-11-22
seems no one is gonna answer, anyway, I got the problem solved under openSUSE with the following steps:
use reiserfs
after system starts stop acpid:
"service acpid stop"
don't disable it, it has to be started then u stop it
that's the only way I was able to solve the Load_Cycle_Count problem without hard disk overheat that's caused if u use hdparm -B 254, don't know why this doesn't work under Ubuntu although it works on other combinations too other than openSUSE like my previous Vector Linux, on Vector the problem actually didn't exist, and that was the first time ever to get rid of this problem, that's because Vector uses reiserfs as default and I didn't try it before that time, however after replacing its kernel (2.6.27 I think) with a new one (2.6.30) compiled from source, the problem happened again, I figured out that I can solve it by stopping acpid after it runs on startup but not by completely disabling it, so it seems new kernels need this additional last step.

to make a lot of ******** short, if u have this ******* stupid problem, try the following:
- use reiserfs for all ur linux partitions
- stop acpid after it starts on startup
of course this doesn't work on ubuntu (that's why I started this thread) and I don't know why

btw, the problem disappears on ubuntu when I start the Oracle service ! I guess because Oracle uses the hard disk a lot and doesn't give it the chance to increase the Load_Cycle_Count

phew!!!, a lot of **** here, I'm very chatty, sorry

---

