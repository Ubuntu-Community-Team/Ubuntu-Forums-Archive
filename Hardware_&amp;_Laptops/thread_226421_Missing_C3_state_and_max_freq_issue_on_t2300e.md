---
title: "Missing C3 state and max_freq issue on t2300e"
date: 2006-07-31
forum: Hardware &amp; Laptops
---

### Post by frankuzzo on 2006-07-31
I just installed the newer smp kernel on ubuntu 6.06 for dual core support of my hp nc6320 laptop with centrino T2300E.
```
# uname -srv
Linux 2.6.15-26-686 #1 SMP PREEMPT Mon Jul 17 20:14:14 UTC 2006
```
I see a couple of problems concerning the cpu:
[LIST=1]
[*]missing C3 state (tried both w/ and w/o power cord):

```
# cat /proc/acpi/processor/CPU?/power
active state:            C2
max_cstate:              C8
bus master activity:     00000000
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010]
   *C2:                  type[C2] promotion[--] demotion[C1] latency[001] usage[03650399]
active state:            C2
max_cstate:              C8
bus master activity:     00000000
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010]
   *C2:                  type[C2] promotion[--] demotion[C1] latency[001] usage[04785659]
```

C3 state was present on the 386 single core kenrnel.

[*] cpu scaling is probably broken. On the 386 default ubuntu 6.06 kernel the only core can be adjusted wrt cpu frequency, and the /proc/cpuinfo is reflecting the different frequencies also with greater bogomips values (i.e. ~2000 @ 1 Ghz, ~3300 @ 1.6 Ghz). Now with the smp kernel freq can not be put higher than 1.3Ghz whatever governor is used. For example via the ```
echo "1667000"> /sys/devices/system/cpu/cpu{1|0}/cpufreq/scaling_max_freq
``` command (i.e with "performance" governor) the result is always:
```
# cat /sys/devices/system/cpu/cpu?/cpufreq/scaling_max_freq
1333000
1333000
```
On /proc/cpuinfo the bogomips reach in that way only 2600 for each cpu (1.3Ghz) instead of 3300. Secondly the "cpu MHz" stays always at 1662.800 instead of changing.[/LIST]

Any tips?
Thanks a lot!

---

### Post by ShinjiLeery on 2006-07-31
I have the same issue too with a P-M laptop:

```
xxxxxxxx:/sys/devices/system/cpu/cpu0/cpufreq$ cat /proc/acpi/processor/CPU1/info
processor id:            0
acpi id:                 1
bus mastering control:   no
power management:        yes
throttling control:      yes
limit interface:         yes

```

And:

```
xxxxxxx:/sys/devices/system/cpu/cpu0/cpufreq$ cat /proc/acpi/processor/CPU1/power
active state:            C2
max_cstate:              C8
bus master activity:     00000000
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010]
   *C2:                  type[C2] promotion[--] demotion[C1] latency[001] usage[00665440]

```

The lowest frequency that i can get is only half of the max freq avviable:

```
xxxxxxxx:/sys/devices/system/cpu/cpu0/cpufreq$ cat scaling_available_frequencies
1596000 1596000 1596000 1596000 1596000 1596000 1596000 1330000 1064000 798000

```

I read in the acpi4linux sit that i can't have the C3 state until i have the bus mastering active. 

What's wrong with the configuration? Tnx for the help

P.S. I work with the 386 kernel, but i have the same problem with the 686 one.

---

### Post by frankuzzo on 2006-07-31
I do have bus mastering... dunno where to look (probably centrino duo is still unsupported by this kernel)

```

# cat /proc/acpi/processor/CPU?/info
processor id:            0
acpi id:                 1
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes
processor id:            1
acpi id:                 2
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes
```

Thanks!

---

### Post by ShinjiLeery on 2006-08-02
Any ideas to activate the C3 state and bus mastering ?

---

### Post by donut on 2006-08-03
FYI, I've posted my CPU ACPI state on the following thread: [http://www.ubuntuforums.org/showthread.php?p=1334767](http://www.ubuntuforums.org/showthread.php?p=1334767)

Paul

---

### Post by frankuzzo on 2006-08-09
Correction to my first post: the C3 state is never present even in the 386 kernel. I see this is a common problem of several core duo laptops. Please post the outputs of the commands "cat /proc/.." and /sys/.. from your laptops.

As regards the max cpu frequency it is adjustable to its maximum *only* in the live cd, even when running on the default 386 kernel i can not make it. 

p.s. A compiled custom kernel let me set correctly the max speed but only when the wireless module is not loaded (!), I don't know where to ](*,) :-k :confused: 

Bye!

---

### Post by amborle on 2006-11-27
Any fixed found for this without recompiling and stuff? Don't even know how to do that? What to add/remove etc?

---

