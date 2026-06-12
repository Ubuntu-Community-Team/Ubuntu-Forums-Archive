---
title: "SMP hyperthreading =&gt; not using all processors..."
date: 2007-11-10
forum: Hardware &amp; Laptops
---

### Post by bss on 2007-11-10
Hi!!

I have just configured my new IBM server which has 2x xeon 1.8 dualcore and I have noticed that when i run a php cli app or access my website in browser, the kernel uses only one processor.

I did a test whit a php script accessing mysql database and i monitored the processes ( php , mysql ). I noticed that both mysql server and php or apache2 ran on only one processor. 

it looked like this:
```
top - 23:33:34 up  3:07,  2 users,  load average: 1.21, 0.58, 0.30
Tasks:  94 total,   2 running,  92 sleeping,   0 stopped,   0 zombie
Cpu0  :  0.7%us,  0.0%sy,  0.0%ni, 99.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  : 99.7%us,  0.3%sy,  0.0%ni,  0.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1035376k total,   218260k used,   817116k free,    17404k buffers
Swap:  1502036k total,        0k used,  1502036k free,    92644k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
11341 www-data  25   0 25772 9720 3436 R  100  0.9   0:12.37 apache2
 4495 mysql     21   0  125m  23m 4840 S    1  2.3   8:00.68 mysqld
    1 root      18   0  2948 1848  532 S    0  0.2   0:01.85 init
    2 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.03 migration/0
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/2
   10 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/2
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/3


```

or

```
top - 23:34:28 up  3:08,  2 users,  load average: 1.01, 0.63, 0.33
Tasks:  98 total,   2 running,  96 sleeping,   0 stopped,   0 zombie
Cpu0  : 38.0%us, 58.3%sy,  0.0%ni,  2.7%id,  1.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu1  :  2.3%us,  0.7%sy,  0.0%ni, 94.3%id,  2.7%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.7%us,  0.3%sy,  0.0%ni, 99.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Cpu3  :  0.0%us,  0.0%sy,  0.0%ni,100.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1035376k total,   218488k used,   816888k free,    17480k buffers
Swap:  1502036k total,        0k used,  1502036k free,    92460k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 4495 mysql     15   0  125m  23m 4840 S   97  2.3   8:06.20 mysqld
14618 root      15   0 18164 7212 4176 S    3  0.7   0:00.18 php
    1 root      18   0  2948 1848  532 S    0  0.2   0:01.85 init
    2 root      11  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.03 migration/0
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/2
   10 root      39  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/2
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.02 migration/3
  
```

With mysql using all of one processor, and php (cli script) runing on the same processor insted of having another processor for itself... This is the "SMP" part of the SMP kernel that I dont understand...

Is there a way to change processor affinity on a process, so thet mysql would have it's own processor and php also?

If not, is there anything that I could do to get better performance..

HW and kernel info:
CPU: 2x Intel xeon 1.8 dulacore, 1gb RAM
Kernel:  2.6.22-14-server SMP i686 // HyperThreading is present in /proc/cpuinfo for all 4 processors/cores

Please HELP!!!

---

