---
title: "[SOLVED] How to disable throttling?"
date: 2008-04-22
forum: Hardware
---

### Post by ene_dene on 2008-04-22
I have laptop with the following processor:
```

ed@killers2:/proc$ cat cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 13
model name      : Intel(R) Pentium(R) M processor 1.70GHz
stepping        : 6
cpu MHz         : 1694.660
cache size      : 2048 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr mce cx8 sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss tm pbe up est tm2
bogomips        : 3391.35

```
I use boinc - einstein@home so I need that my laptop works 100% all the time, with no powersaving, but I can't stop cpu throttling:
```

ed@killers2:/proc/acpi/processor/CPU0$ ls
info  limit  power  throttling
ed@killers2:/proc/acpi/processor/CPU0$ cat throttling
state count:             8
active state:            T2
states:
    T0:                  00%
    T1:                  12%
   *T2:                  25%
    T3:                  37%
    T4:                  50%
    T5:                  62%
    T6:                  75%
    T7:                  87%
ed@killers2:/proc/acpi/processor/CPU0$ cat limit
active limit:            P0:T3
user limit:              P0:T0
thermal limit:           P0:T3
ed@killers2:/proc/acpi/processor/CPU0$ cat info
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      yes
limit interface:         yes
ed@killers2:/proc/acpi/processor/CPU0$ cat power
active state:            C2
max_cstate:              C8
bus master activity:     00000007
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00000010] duration[00000000000000000000]
   *C2:                  type[C2] promotion[C3] demotion[C1] latency[001] usage[00000882] duration[00000000000006781310]
    C3:                  type[C3] promotion[C4] demotion[C2] latency[085] usage[00000000] duration[00000000000000000000]
    C4:                  type[C3] promotion[--] demotion[C3] latency[185] usage[00000000] duration[00000000000000000000]

```
So from that you can see that my comp is not using all the cycles.
I saw a suggestion that I should type:
```
sudo /usr/bin/cpufreq-selector -g performance
```
but the output is:
```
No cpufreq support
```

Please tell me how to disable throttling in some other way.

---

### Post by markjensen on 2008-04-22
There is a 'service' daemon called "powernowd" running that handles this.  You can stop it with a command **sudo /etc/init.d/powernowd stop**
but there may also be a way to do it from the GUI.

That worked for me.  Check your CPU speeds afterward, and it should be full clock at that point.  You can re-start it with "start" as your parameter in the above command.


EDIT: Mind your temps when you do this, especially on a laptop.  Your CPU will run quite a bit warmer, and your laptop may not have been designed to dissipate that much heat without expecting some cooldown period!

---

### Post by ene_dene on 2008-04-22
> **markjensen said:**
> There is a 'service' daemon called "powernowd" running that handles this.  You can stop it with a command **sudo /etc/init.d/powernowd stop**
Unfortunately I haven't got such service installed.

---

### Post by Yellow Pasque on 2008-04-22
Your PC is probably using the speedstep-centrino module for throttling.

Try this:
```
lsmod | grep speedstep
```

If you have the module running, you can stop it from loading by blacklisting it. You'll see how to enter it when you open the file:
```
gksudo gedit /etc/modprobe.d/blacklist
```

---

### Post by ene_dene on 2008-04-23
> **Temüjin said:**
> Your PC is probably using the speedstep-centrino module for throttling.

Try this:
```
lsmod | grep speedstep
```

If you have the module running, you can stop it from loading by blacklisting it. You'll see how to enter it when you open the file:
```
gksudo gedit /etc/modprobe.d/blacklist
```
Yes, that's true. I turned of acpi from loading and that solved the problem. I'll try it this way to, so I don't need to turn of acpi.
Thank you.
Btw, I can't find "mark this thread as solved".

---

