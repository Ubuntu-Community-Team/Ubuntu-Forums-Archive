---
title: "how to get under 600Mhz on Dothan?"
date: 2005-06-22
forum: Hardware &amp; Laptops
---

### Post by ffxffxff on 2005-06-22
i run ubuntu 5.04 on my r50 laptop with m 715 dothan CPU (1,5 Ghz), this one supports 8 throttling states thus the lowest possible speed must be 187,5Mhz. But ACPI only sets up a range between 1500Mhz and 600Mhz (userspace governor), so powernowd can only scale down to 600 Mhz.

how can I extend the scaling frequency table by 187.500 kHz?

before ubuntu, I ran debian on this laptop and it worked fine for 187,5Mhz freq. by default, but it ran with p4 module, not centrino

---

### Post by Zeddicus on 2005-06-22
Hmm... do the other frequencies show up in
```

/sys/devices/system/cpu/cpu0/cpufreq
```?

---

### Post by ffxffxff on 2005-06-22
[QUOTE=Zeddicus]Hmm... do the other frequencies show up in
```

/sys/devices/system/cpu/cpu0/cpufreq
```?[/QUOTE]

yes they're shown there, 6 different ones ranging from 1500000 to 600000. the scaling_driver reports 'centrino', so I think this module returns available frequences, maybe there is a patch for this module, but I did not find any... :(

---

### Post by ffxffxff on 2005-06-22
well, meanwhile i found that throttling is done by module 'speedstep-centrino.ko' on my machine. I wanted to check the source but did not find any kernel-sources for the compiled kernel of ubuntu v5.04. so i got the kernel sources from kernel.org (2.6.11). the 'speedstep-centrino.c' source, that I looked for was also there.


when walking thru code, I noticed that there were table definitions only for BANIAS cpus and the author referenced to Intel's datasheet where he got table-values from. but Intel meanwhile issued other datasheets on CPUs with 2MB L2Cache (dothan) and I compared the table-values in the module with those in intel's spec. 

i found that voltage-values used in the module are higher than described by Intel's datasheet, so I have to recompile the module, but HOW?

if I build the new kernel, it also builds all the modules, but the speedstep-centrino.o - built module does not work this way  :???:

---

### Post by TheRealEdwin on 2005-06-22
Could you do a HOWTO with this? I too have a Dothan (ASUS Z71V laptop) and I am sure others would greatly appreciate this. Currently I can only go down to 798 MHz.

---

### Post by ffxffxff on 2005-06-23
[QUOTE=TheRealEdwin]Could you do a HOWTO with this? I too have a Dothan (ASUS Z71V laptop) and I am sure others would greatly appreciate this. Currently I can only go down to 798 MHz.[/QUOTE]

I dont think a HOWTO can be made at this point - as I still not achieved my aim. but in your case you could look at
```
/sys/devices/system/cpu/cpu0/cpufreq/scaling_driver
``` and tell which driver is responsible for scaling. maybe that scaling is controlled by acpi and not by centrino module.

actually, as taken from the Intel's spec.,  the minimum frequency for all M-CPUs is 600Mhz. But I know that speedswitchXP (scaling tool for XP) goes under 600Mhz if idle. maybe a p4 module could help on linux - i'll try it out.

---

### Post by ffxffxff on 2005-06-27
THROTTLING vs CLOCK/VOLTAGE MODULATION


until now I recompiled "speedstep-centrino.c" with only one valid table to my CPU (M 715, Dothan, 1,5Ghz) after changing the freq/volt. pairs to the minimum (below the recommended settings by Intels' spec,), hope this will save some battery power.

there's also possibilty to throttle the CPU by

first checking the valid throttling states for your CPU by
"# cat /proc/acpi/processor/CPU/throttling"

and finally setting the desired state doing
"# echo -n 7 > /proc/acpi/processor/CPU/throttling"
this would set max. throttling on my Dothan. though throttling only makes sense if you do not use your system, i.e. while readling docs etc.
(throttling does not affect the clock of the CPU, but just lets the CPU only execute opcodes after certain number of clock cycles. i.e. throttling by 50% means that code will only be executed on every second clock cycle - thus a CPU clocked at 1500Mhz would be as efficient as clocked at 750Mhz, although still clocked at 1500 Mhz)


however, I still could not scale the CPU under the 600Mhz threshold :( ....wondering if this is possible at all...

---

