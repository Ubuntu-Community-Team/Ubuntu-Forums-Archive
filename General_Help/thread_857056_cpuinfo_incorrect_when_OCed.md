---
title: "cpuinfo incorrect when OCed"
date: 2008-07-12
forum: General Help
---

### Post by clarknova on 2008-07-12
/proc/cpuinfo doesn't reflect the true frequency of the overclocked cpu, except if you look at 'bogomips'. The true cpu MHz is shown in the bios and cpuz in vista, as well as in dmesg. The 'CPU frequency scaling monitor' applet also shows stock values when overclocked.
```
$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) Dual Core Processor 4050e
stepping	: 2
cpu MHz		: 2100.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 5040.05
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 107
model name	: AMD Athlon(tm) Dual Core Processor 4050e
stepping	: 2
cpu MHz		: 2100.000
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch
bogomips	: 5040.05
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc 100mhzsteps
```
```
$ dmesg | grep -i mhz
[   10.697069] time.c: Detected 2518.203 MHz processor.
[   11.188086] Detected 14.989 MHz APIC timer.
[   13.723899] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[   30.946505] powernow-k8:    0 : fid 0xd (2100 MHz), vid 0xc
[   30.946508] powernow-k8:    1 : fid 0xc (2000 MHz), vid 0xd
[   30.946510] powernow-k8:    2 : fid 0xa (1800 MHz), vid 0xf
[   30.946512] powernow-k8:    3 : fid 0x2 (1000 MHz), vid 0x16
```

Anybody know of a fix? Has this been reported as a bug?

db

---

### Post by happyhamster on 2008-07-12
Try testing cat /proc/cpuinfo when putting the cpu under serious stress (super_pi for example, see: [http://ubuntuforums.org/showthread.php?t=60264](http://ubuntuforums.org/showthread.php?t=60264)). Does the cpu run at its maximum speed in that case?

Anyway, it's likely the powernow-daemon scaling back the cpu. You can disable it from System-->Administration-->Services-->CPU Frequency manager.


[edit; your problem might be related to:

[http://ubuntuforums.org/showthread.php?p=1044836#post1044836](http://ubuntuforums.org/showthread.php?p=1044836#post1044836)

[https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/46384](https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/46384)

So, it could be that powernow just reads cpu frequencies from a fixed table, instead of calculating them from the maximum (overclocked) cpu frequency available.

]

---

### Post by clarknova on 2008-07-14
> **happyhamster said:**
> Try testing cat /proc/cpuinfo when putting the cpu under serious stress...Does the cpu run at its maximum speed in that case?

The CPU reaches its maximum speed, as reflected in the bogomips of cpuinfo above. I have my cpu frequency scaling applet (cpufreq-selector) installed SUID root so I can change the cpu frequency with a click of the mouse. When set to report in frequency it shows the max as 2.1 when it should be 2.52. All other frequencies read as stock instead of stock+20%, which is what it's actually running at.

> your problem might be related to:

[http://ubuntuforums.org/showthread.php?p=1044836#post1044836](http://ubuntuforums.org/showthread.php?p=1044836#post1044836)

[https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/46384](https://bugs.launchpad.net/ubuntu/+source/powernowd/+bug/46384)

I don't have the expertise to say it's totally unrelated, but the symptoms are a bit different.

> So, it could be that powernow just reads cpu frequencies from a fixed table, instead of calculating them from the maximum (overclocked) cpu frequency available.

Exactly what I think is going on. Anybody know if I can change that table manually? Where does it exist besides /proc/sys/..., since I can't change it there?

db

---

### Post by *yH&gt;jw+o! on 2010-12-27
I have the same problem in ubuntu 10.10

Ironicly enough cpuz in wine shows the right clock speed.

---

