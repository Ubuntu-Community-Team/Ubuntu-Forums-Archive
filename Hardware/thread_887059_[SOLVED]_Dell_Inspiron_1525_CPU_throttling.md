---
title: "[SOLVED] Dell Inspiron 1525 CPU throttling"
date: 2008-08-11
forum: Hardware
---

### Post by squaregoldfish on 2008-08-11
I've got a shiny new Dell Inspiron 1525. I installed cpufreq for CPU speed control, but it doesn't work - there's no driver installed to handle the Celeron processor.

Instead, I've found the CPU throttling file in

/proc/acpi/processor/CPU0

and it looks like there's a number of processor throttling options in there. However, I don't seem to be able to change it at all. 'cat'ing the file gives the following:

```
state count:             8
active state:            T0
state available: T0 to T7
states:
   *T0:                  100%
    T1:                  87%
    T2:                  75%
    T3:                  62%
    T4:                  50%
    T5:                  37%
    T6:                  25%
    T7:                  12%

```

but attempting to echo any of the states into the file (that's how I understand this to work) doesn't have any effect - my CPU is always in state T0.

Does anyone know how this is supposed to work, or what I might be doing wrong?

Of course, if anyone has got cpufreq to work with this laptop, I'd be interested to hear it!

Thanks,
Steve.

---

### Post by jimihieu on 2008-08-14
Hi,
I am using ubuntu 8.04 and new to linux.
I jst install linux inside my vista
Would someone show me how to activate/inactivate my buit-in webcam, mousepad and wireless card?

thank you

---

### Post by squaregoldfish on 2008-08-28
Ignoring the random post above, I've discovered that I don't need to solve my problem. Having plugged an electricity usage meter into the laptop, I've noticed that the CPU automatically draws less power when it's not under load, so it doesn't need any explicit OS support for that feature. Which is nice.

Steve.

---

### Post by juamez. on 2009-03-25
As you should be aware of, the lack of cpu frequency scaling (not throttling) does not result in a 100% load all the time. Mostly it's the load that causes the power usage, not the clock at which the cpu is currently at. Lowering the frequency while the cpu has nothing to do will further lower the power usage by a bit, but not very much. It is rather a battery-saving feature, to gain a couple of minutes.

---

