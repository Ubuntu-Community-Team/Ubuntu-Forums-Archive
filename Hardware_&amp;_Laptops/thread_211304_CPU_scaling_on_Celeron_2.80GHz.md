---
title: "CPU scaling on Celeron 2.80GHz"
date: 2006-07-08
forum: Hardware &amp; Laptops
---

### Post by mpalla on 2006-07-08
Hi everybody,

I configured CPU Frequency Scaling for my [Pavilion ze5702ea]("http://www.ubuntuforums.org/showthread.php?t=193506"), following [this howto]("http://www.ubuntuforums.org/showthread.php?t=190921"), and it seems to work, in fact now the CPU Frequency Monitor applet shows 2.10GHz instead of the full frequency.

The problem is, why it doesn't go anywhere down that frequency? It seems that uses 2.10GHz with low cpu load (up to 10-15%?) and then the full 2.80GHz. There's something more that I have to configure or it's a software bug?

Some more information:

[COLOR="Red"]**cat /proc/cpuinfo**[/COLOR]
```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Celeron(R) CPU 2.80GHz
stepping        : 9
cpu MHz         : 2791.288
cache size      : 128 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe cid xtpr
bogomips        : 5592.64

```

[COLOR="Red"]**cat /proc/acpi/processor/CPU0/info**[/COLOR]
```
processor id:            0
acpi id:                 0
bus mastering control:   yes
power management:        yes
throttling control:      no
limit interface:         no

```

[COLOR="Red"]**cat /proc/acpi/processor/CPU0/power**[/COLOR]
```
active state:            C2
max_cstate:              C8
bus master activity:     00000000
states:
    C1:                  type[C1] promotion[C2] demotion[--] latency[000] usage[00224860]
   *C2:                  type[C2] promotion[--] demotion[C1] latency[099] usage[54726134]

```

but both [COLOR="Red"]**cat /proc/acpi/processor/CPU0/limit**[/COLOR] and [COLOR="Red"]**cat /proc/acpi/processor/CPU0/throttling**[/COLOR] show```
<not supported>
```

Any idea?

EDIT: according to the applet, it seems that passing from 100% (2.80GHz) to 75% (2.10GHz) it uses briefly another step, 2.45GHz (87%).

---

### Post by mpalla on 2006-12-08
After some upgrade (or maybe some other addon I have installed?), the CPU Frequency Scaling did work correctly on Dapper, recognizing and using all the 9 frequencies.
And this just adding the p4_clockmod and nothing more (apart from a misterious fix downloaded during an update).

Unfortunately, now I've installed Edgy instead of Dapper, and the very same problem has appeared again: only 3 freqs recognized and used, as in Dapper at the beginning.

In [this]("http://www.ubuntuforums.org/showpost.php?p=1854895&postcount=11") post you can find the latest details. Does anyone else experience the same problem, or I am the only one still using a Celeron :) ?
Is it possible that there is a bug or something like that, or I am missing some configuration?

Thank you in advance!

---

