---
title: "Continuous HD Fan on 16.04; not on 14.04 or Win 10"
date: 2016-05-21
forum: Hardware
---

### Post by flyingsolo on 2016-05-21
On my Desktop, I have had dual boot of Ubuntu 14.04 and Win 10 and now recently added 16.04 to trial it.
However, the fan runs continuously when I'm in 16.04 which is not a problem in the other 2 OS's.
I haven't the slightest idea why or how to troubleshoot this and any ideas would be appreciated!

(BTW, I had posted the same question under General questions forum but no real responses there so thought Hardware might be a better forum for it.)

---

### Post by Linuxisfast on 2016-05-21
Can you list your hardware?

---

### Post by flyingsolo on 2016-05-21
Sure, but how extensive information were you thinking? 
Running; lshw shows an awful lot of detail but is there a contracted list that would suit? Another command for instance?
thanks,

---

### Post by Linuxisfast on 2016-05-21
Just basic CPU, GPU and drivers installed if any. Also are you monitoring CPU speed via Psensor?

---

### Post by flyingsolo on 2016-05-21
/0/1                       processor      Intel(R) Core(TM) i5-2320 CPU @ 3.00GH
/0/100                     bridge         2nd Generation Core Processor Family D
/0/100/1                   bridge         Xeon E3-1200/2nd Generation Core Proce
/0/100/1/0                 display        GF108 [GeForce GT 530]
/0/100/1/0.1               multimedia     GF108 High Definition Audio Controller

Hopefully, that's the sort of info you were thinking of.

---

### Post by Linuxisfast on 2016-05-22
Great can you check in system monitor if any process is taking up CPU load constantly?

---

### Post by flyingsolo on 2016-05-22
Yes, I already did that but there are no 'heavy uses' documented on System Monitor. The fan is continuously on even if  the computer is idle or just average web browsing with no special programs running.
I'm guessing it has something to do with whatever drivers/systems are controlling the fan. Maybe it's set to a ridiculously low processor temperature? I don't really know how to access that sort of stuff.

---

### Post by gianluca3 on 2016-05-26
I have a similar problem,

Updating from 14.04 to 16.04 and now the fan are always running with a low temperature (checked with the command sensors and with the hand...) and no process taking more than 1-2% of CPU load (checked with the command top)

If I run pwmconfig I receive

> /usr/sbin/pwmconfig: There are no fan-capable sensor modules installed


my CPU

> lscpu
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                8
On-line CPU(s) list:   0-7
Thread(s) per core:    2
Core(s) per socket:    4
Socket(s):             1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 26
Model name:            Intel(R) Core(TM) i7 CPU         950  @ 3.07GHz
Stepping:              5
CPU MHz:               2667.000
CPU max MHz:           2668,0000
CPU min MHz:           1600,0000
BogoMIPS:              5346.44
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              8192K
NUMA node0 CPU(s):     0-7
Flags:                 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm tpr_shadow vnmi flexpriority ept vpid dtherm ida


my GPU
> lspci -vnn | grep VGA -A 12
0a:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108 [GeForce GT 630] [10de:0f00] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: ZOTAC International (MCO) Ltd. GF108 [GeForce GT 630] [19da:6199]
    Flags: bus master, fast devsel, latency 0, IRQ 41
    Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
    Memory at d8000000 (64-bit, prefetchable) [size=128M]
    Memory at d6000000 (64-bit, prefetchable) [size=32M]
    I/O ports at ec00 [size=128]
    Expansion ROM at fbd80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nouveau
    Kernel modules: nvidiafb, nouveau

0a:00.1 Audio device [0403]: NVIDIA Corporation GF108 High Definition Audio Controller [10de:0bea] (rev a1)


thanks in advance g.

---

### Post by Linuxisfast on 2016-05-29
Have you tried shutting off nvidia with nvidia-prime in the driver?

---

### Post by gianluca3 on 2016-06-17
sorry for the late reply, major issues also beyond linux..., the fan always on was the one related to the graphic card and it has been solved by "playing" around with the drivers.

i do not have the details right now, just contact me and i will post all

hanks
g.

---

