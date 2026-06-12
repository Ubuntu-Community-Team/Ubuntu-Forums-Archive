---
title: "Intermittent poor performance, low CPU frequency, Thermal throttling?"
date: 2020-04-01
forum: Hardware
---

### Post by andrewlinux on 2020-04-01
I recently brought a Lenovo laptop with an AMD APU (A4-9120e) the performance varies wildly. For example it will be good for 20 minutes then slow to a crawl on the same task. It seems to be because the frequency is lowered due to thermal throttling, although I have never seen the temperature higher than 54 degrees Celsius. The frequency jumps between 800MHz and 1500MHz, it's meant to have a base rate of 1500MHz and a turbo speed of 2200MHz.

Like I said it never actually gets hot, if it did I would see this as a hardware design fault and give up.

Can anyone help? Any input would be much appreciated.

Using Ubuntu 18.04. (I've tried various distributions with the same results.)

---

### Post by Doug S on 2020-04-02
That processor has a fairly low TDP (Thermal Design Power). It might be power throttling.

Note: I only know Intel processors. They will power throttle by themselves. Not sure if the same applies to AMD processors.

While I have heard that turbostat (linux-tools-common package) works with some AMD processors, I have no personal experience.

Example (i5-9600K with TDP set to 50 watts) 5 seconds per sample:

From turbostat startup listing of limits and configurations:

```
cpu0: MSR_PKG_POWER_LIMIT: 0x4283e800dd8190 (UNlocked)
cpu0: PKG Limit #1: ENabled ([COLOR="#FF0000"]50.000000 Watts, 28.000000 sec,[/COLOR] clamp ENabled)
cpu0: PKG Limit #2: ENabled (125.000000 Watts, 0.002441* sec, clamp DISabled)

```

```

sudo ~/[COLOR="#FF0000"]turbostat --Summary --interval 5 --show Avg_MHz,Busy%,Bzy_MHz,IRQ,PkgTmp,PkgWatt[/COLOR]
...delete big spew of stuff (relevant part above) ...
Avg_MHz Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt
1       0.08    850     273     30      2.17
1       0.08    826     220     31      1.98
0       0.05    [COLOR="#FF0000"]832[/COLOR]     157     31      2.00 [COLOR="#FF0000"]<<< System idle[/COLOR]
1       0.07    833     192     30      1.95
8       0.30    2542    633     31      2.23
1       0.06    836     243     31      1.97
15      0.50    3062    614     31      2.20
1       0.08    829     236     31      1.98
0       0.06    827     196     31      1.93
1       0.08    859     199     31      1.95
1       0.08    838     202     31      2.03
2309    54.91   4204    6477    63      64.93
4168    99.07   4207    11313   63      116.27 [COLOR="#FF0000"]<<< Extreme CPU load applied**[/COLOR]
4165    99.09   4203    11307   63      116.05 
3669    99.66   3681    11231   44      83.51
3147    100.24  [COLOR="#FF0000"]3139[/COLOR]    11285   44      49.75 [COLOR="#FF0000"]<<< Package Power reduced via maximum CPU frequency throttling by the processor itself.[/COLOR]
3147    100.24  3139    11305   44      49.83
3145    100.24  3137    11286   45      49.87
3146    100.24  3138    11306   45      49.91
3146    100.24  3138    11299   44      49.90
3144    100.24  3136    11289   45      49.95
3145    100.24  3138    11298   46      49.91
3143    100.24  3136    11287   45      49.94

```

** There are a great number of "CPU stressing" type programs and methods. I have also written many myself. By far, the best method I have found is the heat/torture test in prime95, and that was used here.

---

