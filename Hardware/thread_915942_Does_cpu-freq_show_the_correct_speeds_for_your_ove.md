---
title: "Does cpu-freq show the correct speeds for your overclocked cpu??"
date: 2008-09-10
forum: Hardware
---

### Post by e-dard on 2008-09-10
Hello all,

I have a problem with my reported cpu speed in Ubuntu.  Basically, I have a core-2 duo 1.86Ghz (E6300 I think).  I have overclocked it to 2.38 Ghz using the bios, it works fine...

Basically, the cpu frequency monitor always shows the cpu as running in powersave mode (1.6Ghz) or full mode (1.86Ghz).  However, I am convinced that the overclock is successful.  Here is some proof using super pi to calculate pi to 1 million places.

STOCK SPEED -- powersave mode (reported 1.6, actually 1.6Ghz) superpi 1million.
```
 I=19 L=   89415        Time=       1.120 Sec.
 End of main loop
 End of calculation.    Time=      25.378 Sec.
 End of data output.    Time=       0.156 Sec.
 Total calculation(I/O) time=      25.534(       0.928) Sec.
```

STOCK SPEED -- full mode (reported 1.86, actually 1.86Ghz) pi 1mil.
```
 I=19 L=   89415        Time=       1.000 Sec.
 End of main loop
 End of calculation.    Time=      22.405 Sec.
 End of data output.    Time=       0.132 Sec.
 Total calculation(I/O) time=      22.537(       0.856) Sec.
```

Ok, and now with the overclock on (FSB = 340, mult = 7 --> 2.38Ghz

OVERCLOCK -- powersave (reported 1.6, actual ????) pi 1mil.
```
 I=19 L=   89415        Time=       0.932 Sec.
 End of main loop
 End of calculation.    Time=      20.805 Sec.
 End of data output.    Time=       0.120 Sec.
 Total calculation(I/O) time=      20.925(       0.756) Sec.
```

OVERCLOCK -- full (reported 1.83, actual 2.38Ghz (i hope!!)) pi 1mil.
```
 I=19 L=   89415        Time=       0.820 Sec.
 End of main loop
 End of calculation.    Time=      18.309 Sec.
 End of data output.    Time=       0.112 Sec.
 Total calculation(I/O) time=      18.421(       0.688) Sec.
```

As you can all see there is a drastic decrease in calculation time.  This shows that the cpu is overclocked successfully.  In the stock case running on full speed results in about a 12% increase over powersave mode.  When overclocked, running on full also results in about a 12% increase over the powesave mode.  Thus, I guestimate that the speed of the overclocked processor in powersave mode is:

```
(1.6/1.86) * 2.38 = 2.04Ghz
```

Probably not far from that.  Anyway, we can see that the overclock is fine but the OS can't give the correct speeds--it is no doubt pulling the values off the chip.

I would like to use throttling because it helps to keep temps down and reduce energy consumption.  However, it would be nice if it did actually read my cpu speed, rather than use the stock labels!

Some possibly relevant cpu things I have installed:

dpkg -l | grep cpu
```
ii  cpufrequtils                         002-7.2                          utilities to deal with the cpufreq Linux ker
ii  libcpufreq0                          002-7.2                          shared library to deal with the cpufreq Linu
ii  time                                 1.7-21                           The GNU time program for measuring cpu resou

```

dpkg -l | grep acpi
```
ii  acpi-support-base                    0.109-5                          scripts for handling base ACPI events such a
ii  acpid                                1.0.6-10                         Utilities for using ACPI power management

```

Anyone got any thoughts on this??

Cheers,
e-dard

---

### Post by dbenc on 2009-05-05
i believe i have this problem as well, has anyone found a solution yet? this is on a core 2 q6600, overclocked in BIOS ...

---

