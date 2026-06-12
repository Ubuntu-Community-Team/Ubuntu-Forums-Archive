---
title: "Older CPU out-pacing newer one"
date: 2021-09-14
forum: Hardware
---

### Post by bradleypariah on 2021-09-14
I own two laptops, but one of them has much nicer hardware (bigger screen, touch screen, 10-key, backlit keys, etc).
Unfortunately, my "nicer" laptop is unbearably slow, even though it supposedly has faster hardware inside as well.

My supposedly "good" laptop is a Lenovo Flex 3.  It has an i7-5500U dual-core 4-thread @ 2.4GHz, 8GB of RAM, and an SSD.
My "old" laptop, that can run circles around the "good" laptop, is an HP  EliteBook 2540p with an i7 L640 dual-core 4-thread @ 2.13GHz, 6GB of  RAM, and an SSD.
They both are running Kubuntu 21.04.

My HP can open Firefox and have my homepage loaded in under 6 seconds.
My Lenovo takes between 14 and 23 seconds to reach the same site.
EVERYTHING on the Lenovo takes longer.
If I tap the Super key, the Application Dashboard takes five seconds to open.  On the HP, it's practically instantaneous.
The Lenovo doesn't have any stability issues whatsoever, so I don't understand what could be wrong.  
I've tried reinstalling Kubuntu, and even trying other distros, but it's always slow.

Anybody have an idea why?  According to userbenchmarks' website, the  5500U should be 32% faster than the L640, but it's more than the  opposite.  The L640 is zippy as all get out, and the Lenovo feels like a  twenty-five-year old machine.
If the Lenovo is experiencing hardware issues, why doesn't it ever crash?  It's temps never get above 44**°**C, but the CPU usage on that machine is constantly pegged whenever a single app is open.
If Discover is updating, and I try to launch another app, it won't even open till Discover's finished.

[IMG]https://www.kubuntuforums.net/attachment.php?attachmentid=9529&d=1631671110[/IMG]

---

### Post by mikewhatever on 2021-09-15
My idea is, you need to investigate more, and add a bare minimum of useful tech info for review:

> lscpu
glxinfo -B
free -m


If you don't know which processes peg the CPU, redirect top output to a file, and post its contents:

> top -b -n1 > top-output

No screenshots please, just copy/paste the outputs.

---

### Post by TheFu on 2021-09-15
So ... the passmarks on both these systems are pretty low for Core i7 systems.  I have a $50 Pentium desktop CPU - G3258 - from 2015 that is between these in performance.

i7-5500U - 2726
i7-L640 - 1680
G3258 - 2057

A $305 laptop with a Core i5-8258U has 5944 passmarks.  Just sayin'.  Core i7s from the last 2-3 yrs should be in the 16K passmark area.
BTW, the passmark guys routinely rework their numbers so any comparisons are only valid within the same search.  Last year, the G3258 passmarks was over 3600 - as newer CPUs get faster, they tweak the benchmark and all older CPUs ratings are shifted down. I remember a Celeron 2995U in a chromebook was around 1470 passmarks. Just checked that now and it lists around 800.  I ran virtual machines on that chromebook!  It worked fine - except the RAM limitations.

All sorts of things go into what makes a system fast or slow.  A failing disk or corrupted file system or slow DNS can impact perceived performance.  It is unlikely we will be able to see things by posting commands on a forum.  I know the forum moderation team has been working on a "system information" script to help troubleshoot all things Ubuntu, but it isn't quite ready.  You could run **inxi -Fxxxxz** and post that output as a start.  

It won't be able to see any hardware issues.  Only you can see that.  Check the system log files for errors and warnings.  I'd use 
**sudo    egrep    -i      'erro|warn'      /var/log/*log**
and look over that output.  There really should only be a few lines. If there are more, redirect the output to a file and use your favorite editor to look more closely.  The **journalctl** command can do some searches for system logs too.

---

### Post by oldfred on 2021-09-15
Do you have latest firmware for both UEFI and SSD?
That can make a difference.

Some settings also can help, not just boot.
Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453)

---

### Post by Doug S on 2021-09-15
> **bradleypariah said:**
> Unfortunately, my "nicer" laptop is unbearably slow, even though it supposedly has faster hardware inside as well....
It's temps never get above 44**°**C, but the CPU usage on that machine is constantly pegged whenever a single app is open.
"pegged" doesn't tell the whole story, as we would need to also know the CPU frequency. I wonder if your computer is throttling for some reason. I would suggest to run turbostat (linux-tools-common package, I think). I pretty much always have this command running in a terminal:

```
doug@s19:~/tmp/support-info$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt,CorWatt --interval 6
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt CorWatt GFXWatt RAMWatt
0.02    1840    368     32      1.36    0.70    0.00    0.89
0.02    809     273     32      1.34    0.67    0.00    0.89
0.01    991     233     32      1.34    0.67    0.00    0.89
0.02    806     234     32      1.33    0.67    0.00    0.89
0.02    867     267     32      1.33    0.67    0.00    0.89
52.43   4528    45869   65      71.43   70.78   0.00    0.89
98.69   4530    85636   65      133.62  132.97  0.00    0.89 <<< Power limit 2 throttling
98.69   4530    85614   66      133.76  133.11  0.00    0.89
98.69   4530    85615   67      133.81  133.15  0.00    0.89
99.56   4487    86012   66      125.61  124.96  0.00    0.89
99.60   4479    86587   66      124.93  124.26  0.00    0.89  <<< Power limit 1 throttling
99.60   4479    86089   67      124.91  124.25  0.00    0.89
99.59   4477    86017   66      124.90  124.25  0.00    0.89
99.58   4475    86011   69      124.91  124.26  0.00    0.89
45.53   4474    39860   39      57.90   57.23   0.00    0.89
0.02    838     331     39      1.33    0.67    0.00    0.89

```
I can get the power limits by also running turbostat, but without the --quiet option:
```
...
cpu0: PKG Limit #1: ENabled (125.000000 Watts, 8.000000 sec, clamp ENabled)
cpu0: PKG Limit #2: ENabled (136.000000 Watts, 0.002441* sec, clamp DISabled)...
```

---

### Post by TheFu on 2021-09-15
Any thermal throttling will show up in the system log files.  

I had a 1st gen Core i7 that would throttle 2 cores. I put up with it for a few months, then cleaned out the case from all the dust, cleaned the CPU cooling fan blades and copper heatsink, then cleaned and replaced the thermal grease between the CPU and the heatsink.  After all that, no more throttling.

If you have pets, more gunk will get inside there.  Even without pets, in a filtered house, dust and gunk gets into computers.

---

### Post by bradleypariah on 2021-09-15
Thank you everyone for the suggestions.  Unfortunately I am about to jump on a plane, and I'm not going to take the Lenovo with me on this trip, since I won't have any time to mess with it.  I'll dig into this next week. I appreciate everyone's guidance.

---

### Post by TheFu on 2021-09-15
> **bradleypariah said:**
> Thank you everyone for the suggestions.  Unfortunately I am about to jump on a plane, and I'm not going to take the Lenovo with me on this trip, since I won't have any time to mess with it.  I'll dig into this next week. I appreciate everyone's guidance.

An easy troubleshooting technique is to create a Live-Boot environment, boot off that and see how fast things are.  Obviously, the media used for the ISO will matter, but USB3 flash and USB3-SSD storage should be pretty good. Then compare the performance of each laptop.  This will tell us if it is something in YOUR installed setup on computer-A or computer-B or not.  

If both laptops perform acceptable, then it is just settings.  

Next, create a new userids on both systems and do the same tests with the new users.  If those are fast and the older userids are slow, now you've narrowed down the problem to be just settings for 1 userid on 1 computer.  You can rename a few key directories in your HOME for each userid to see which impacts performance.

But it all starts by figuring out if this is OS, OS-settings, userid or userid-settings related.  Need to narrow those aspects down first.

I'd recommend having a watch near and some paper, so you can create a table of action--> time for each different configuration.  Facts, not "it feels slow". That's important too. You already did that with 5s and 24s posts, but you'll need to compare many other launches.  Try boot, different applications, note which sort of package they were installed from - is it a .deb package, snap, flatpak, appimage or something else?  That all matters too.  There were complaints about snaps loading slowly last year.  The fix for that could make some systems boot slower and use more RAM.

Also, not all SSDs are created equal, so the interface type and nominal performance you typically see would be important to know. There is theory and there are real-world numbers.

---

### Post by bradleypariah on 2021-09-21
> **mikewhatever said:**
> My idea is, you need to investigate more, and add a bare minimum of useful tech info for review

```
[FONT=monospace][COLOR=#54ff54]**bradley@Flex-3-1570**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ lscpu [/COLOR]
Architecture:                    x86_64 
CPU op-mode(s):                  32-bit, 64-bit 
Byte Order:                      Little Endian 
Address sizes:                   39 bits physical, 48 bits virtual 
CPU(s):                          4 
On-line CPU(s) list:             0-3 
Thread(s) per core:              2 
Core(s) per socket:              2 
Socket(s):                       1 
NUMA node(s):                    1 
Vendor ID:                       GenuineIntel 
CPU family:                      6 
Model:                           61 
Model name:                      Intel(R) Core(TM) i7-5500U CPU @ 2.40GHz 
Stepping:                        4 
CPU MHz:                         500.000 
CPU max MHz:                     3000.0000 
CPU min MHz:                     500.0000 
BogoMIPS:                        4788.57 
L1d cache:                       64 KiB 
L1i cache:                       64 KiB 
L2 cache:                        512 KiB 
L3 cache:                        4 MiB 
NUMA node0 CPU(s):               0-3 
Vulnerability Itlb multihit:     KVM: Mitigation: VMX unsupported 
Vulnerability L1tf:              Mitigation; PTE Inversion 
Vulnerability Mds:               Mitigation; Clear CPU buffers; SMT vulnerable 
Vulnerability Meltdown:          Mitigation; PTI 
Vulnerability Spec store bypass: Mitigation; Speculative Store Bypass disabled via prctl and seccomp 
Vulnerability Spectre v1:        Mitigation; usercopy/swapgs barriers and __user pointer sanitization 
Vulnerability Spectre v2:        Mitigation; Full generic retpoline, IBPB conditional, IBRS_FW, STIBP conditional, RSB filling 
Vulnerability Srbds:             Mitigation; Microcode 
Vulnerability Tsx async abort:   Not affected 
Flags:                           fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx  
                                 fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts re 
                                 p_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl est tm 
                                 2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes 
                                  xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs 
                                  ibpb stibp fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid rdseed adx smap intel_pt xsa 
                                 veopt dtherm ida arat pln pts md_clear flush_l1d[/FONT]
```
```
[FONT=monospace][COLOR=#54ff54]**bradley@Flex-3-1570**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ glxinfo -B [/COLOR]
name of display: :0 
display: :0  screen: 0 
direct rendering: Yes 
Extended renderer info (GLX_MESA_query_renderer): 
    Vendor: Intel (0x8086) 
    Device: Mesa Intel(R) HD Graphics 5500 (BDW GT2) (0x1616) 
    Version: 21.0.3 
    Accelerated: yes 
    Video memory: 3072MB 
    Unified memory: yes 
    Preferred profile: core (0x1) 
    Max core profile version: 4.6 
    Max compat profile version: 4.6 
    Max GLES1 profile version: 1.1 
    Max GLES[23] profile version: 3.2 
OpenGL vendor string: Intel 
OpenGL renderer string: Mesa Intel(R) HD Graphics 5500 (BDW GT2) 
OpenGL core profile version string: 4.6 (Core Profile) Mesa 21.0.3 
OpenGL core profile shading language version string: 4.60 
OpenGL core profile context flags: (none) 
OpenGL core profile profile mask: core profile 

OpenGL version string: 4.6 (Compatibility Profile) Mesa 21.0.3 
OpenGL shading language version string: 4.60 
OpenGL context flags: (none) 
OpenGL profile mask: compatibility profile 

OpenGL ES profile version string: OpenGL ES 3.2 Mesa 21.0.3 
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.20[/FONT]
```

```
[FONT=monospace][COLOR=#54ff54]**bradley@Flex-3-1570**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ free -m  [/COLOR]
              total        used        free      shared  buff/cache   available 
Mem:           7857        1271        4896         310        1689        6023 
Swap:          9534           0        9534
[/FONT]
```

> **mikewhatever said:**
> If you don't know which processes peg the CPU, redirect top output to a file, and post its contents:

What I mean to say ius that launching an application like Firefox pegs all CPUs while the program is launching.  They do not remain at 100%.

```
top - 16:14:38 up 24 min,  3 users,  load average: 1.73, 1.72, 1.31
Tasks: 203 total,   1 running, 202 sleeping,   0 stopped,   0 zombie
%Cpu(s):  9.3 us, 11.6 sy,  0.0 ni, 79.1 id,  0.0 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   7857.6 total,   4876.5 free,   1286.4 used,   1694.7 buff/cache
MiB Swap:   9535.0 total,   9535.0 free,      0.0 used.   6004.7 avail Mem 

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
   1249 bradley   20   0 1895308 155980 101900 S  10.5   1.9   2:25.87 kwin_x11
   2811 bradley   20   0   12796   3872   3396 R  10.5   0.0   0:00.07 top
    636 root      20   0    2556    888    800 S   5.3   0.0   0:00.40 acpid
    801 root      20   0  938840 103620  72804 S   5.3   1.3   2:25.89 Xorg
   1315 bradley   20   0 3073872 267424 150300 S   5.3   3.3   2:35.21 plasmashell
   1463 bradley   20   0    4396   2584   2328 S   5.3   0.0   0:23.67 ksysguardd
   1531 bradley   20   0 3470772 546056 189164 S   5.3   6.8   6:43.30 firefox
   1608 bradley   20   0 2502392 165068 103564 S   5.3   2.1   1:45.13 Web Content
      1 root      20   0  166156  12636   7980 S   0.0   0.2   0:11.36 systemd
      2 root      20   0       0      0      0 S   0.0   0.0   0:00.02 kthreadd
      3 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_gp
      4 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 rcu_par_gp
      6 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/0:0H-events_highpri
      9 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 mm_percpu_wq
     10 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_tasks_rude_
     11 root      20   0       0      0      0 S   0.0   0.0   0:00.00 rcu_tasks_trace
     12 root      20   0       0      0      0 S   0.0   0.0   0:00.33 ksoftirqd/0
     13 root      20   0       0      0      0 I   0.0   0.0   0:03.95 rcu_sched
     14 root      rt   0       0      0      0 S   0.0   0.0   0:00.03 migration/0
     15 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/0
     16 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/0
     17 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/1
     18 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/1
     19 root      rt   0       0      0      0 S   0.0   0.0   0:00.49 migration/1
     20 root      20   0       0      0      0 S   0.0   0.0   0:00.24 ksoftirqd/1
     22 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/1:0H-events_highpri
     23 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/2
     24 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/2
     25 root      rt   0       0      0      0 S   0.0   0.0   0:00.51 migration/2
     26 root      20   0       0      0      0 S   0.0   0.0   0:00.19 ksoftirqd/2
     28 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/2:0H-events_highpri
     29 root      20   0       0      0      0 S   0.0   0.0   0:00.00 cpuhp/3
     30 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 idle_inject/3
     31 root      rt   0       0      0      0 S   0.0   0.0   0:00.50 migration/3
     32 root      20   0       0      0      0 S   0.0   0.0   0:00.12 ksoftirqd/3
     34 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/3:0H-kblockd
     35 root      20   0       0      0      0 S   0.0   0.0   0:00.01 kdevtmpfs
     36 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 netns
     37 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 inet_frag_wq
     38 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kauditd
     39 root      20   0       0      0      0 S   0.0   0.0   0:00.00 khungtaskd
     40 root      20   0       0      0      0 S   0.0   0.0   0:00.00 oom_reaper
     41 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 writeback
     42 root      20   0       0      0      0 S   0.0   0.0   0:00.14 kcompactd0
     43 root      25   5       0      0      0 S   0.0   0.0   0:00.00 ksmd
     44 root      39  19       0      0      0 S   0.0   0.0   0:00.00 khugepaged
     91 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kintegrityd
     92 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kblockd
     93 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 blkcg_punt_bio
     94 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 tpm_dev_wq
     95 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 ata_sff
     98 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 md
     99 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 edac-poller
    100 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 devfreq_wq
    101 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 watchdogd
    102 root      20   0       0      0      0 I   0.0   0.0   0:00.93 kworker/u16:1-ext4-rsv-conversion
    103 root       0 -20       0      0      0 I   0.0   0.0   0:00.32 kworker/0:1H-kblockd
    105 root      20   0       0      0      0 S   0.0   0.0   0:00.00 kswapd0
    106 root      20   0       0      0      0 S   0.0   0.0   0:00.00 ecryptfs-kthrea
    108 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kthrotld
    109 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 acpi_thermal_pm
    111 root      20   0       0      0      0 I   0.0   0.0   0:00.02 kworker/0:2-events
    112 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 vfio-irqfd-clea
    114 root       0 -20       0      0      0 I   0.0   0.0   0:00.45 kworker/1:1H-events_highpri
    115 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 ipv6_addrconf
    124 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kstrp
    127 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 zswap-shrink
    128 root       0 -20       0      0      0 I   0.0   0.0   0:04.88 kworker/u17:0-i915_flip
    135 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 charger_manager
    159 root       0 -20       0      0      0 I   0.0   0.0   0:00.55 kworker/2:1H-kblockd
    186 root     -51   0       0      0      0 S   0.0   0.0   0:05.63 irq/28-INT33D1:
    187 root      20   0       0      0      0 S   0.0   0.0   0:00.00 scsi_eh_0
    188 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 scsi_tmf_0
    189 root      20   0       0      0      0 S   0.0   0.0   0:00.00 scsi_eh_1
    190 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 scsi_tmf_1
    191 root      20   0       0      0      0 S   0.0   0.0   0:00.00 scsi_eh_2
    192 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 scsi_tmf_2
    193 root      20   0       0      0      0 S   0.0   0.0   0:00.00 scsi_eh_3
    194 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 scsi_tmf_3
    196 root      20   0       0      0      0 I   0.0   0.0   0:01.12 kworker/u16:4-events_unbound
    198 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 cryptd
    219 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 card0-crtc0
    220 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 card0-crtc1
    221 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 card0-crtc2
    222 root       0 -20       0      0      0 I   0.0   0.0   0:00.35 kworker/3:1H-events_highpri
    270 root      20   0       0      0      0 S   0.0   0.0   0:00.16 jbd2/sda2-8
    271 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 ext4-rsv-conver
    314 root      19  -1   56676  24400  23212 S   0.0   0.3   0:02.32 systemd-journal
    339 root      20   0       0      0      0 I   0.0   0.0   0:00.13 kworker/3:3-events
    346 root      20   0   23784   6364   4140 S   0.0   0.1   0:01.82 systemd-udevd
    351 root       0 -20       0      0      0 S   0.0   0.0   0:00.00 loop0
    355 root       0 -20       0      0      0 S   0.0   0.0   0:00.00 loop1
    357 root       0 -20       0      0      0 S   0.0   0.0   0:00.00 loop2
    361 root       0 -20       0      0      0 S   0.0   0.0   0:00.00 loop3
    362 root       0 -20       0      0      0 S   0.0   0.0   0:00.00 loop4
    371 root       0 -20       0      0      0 S   0.0   0.0   0:00.05 loop5
    383 root       0 -20       0      0      0 S   0.0   0.0   0:00.00 loop6
    386 root       0 -20       0      0      0 S   0.0   0.0   0:00.01 loop7
    392 root       0 -20       0      0      0 S   0.0   0.0   0:00.00 loop8
    397 root       0 -20       0      0      0 S   0.0   0.0   0:00.00 loop9
    404 root       0 -20       0      0      0 S   0.0   0.0   0:00.00 loop10
    405 root       0 -20       0      0      0 S   0.0   0.0   0:00.01 loop11
    406 root       0 -20       0      0      0 S   0.0   0.0   0:00.01 loop12
    407 root       0 -20       0      0      0 S   0.0   0.0   0:00.00 loop13
    408 root       0 -20       0      0      0 S   0.0   0.0   0:00.00 loop14
    409 root       0 -20       0      0      0 S   0.0   0.0   0:00.00 loop15
    410 root       0 -20       0      0      0 S   0.0   0.0   0:00.00 loop16
    411 root       0 -20       0      0      0 S   0.0   0.0   0:00.01 loop17
    422 root     -51   0       0      0      0 S   0.0   0.0   0:00.00 irq/48-mei_me
    577 root      20   0       0      0      0 S   0.0   0.0   0:00.36 jbd2/sda4-8
    578 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 ext4-rsv-conver
    601 systemd+  20   0   24236  13052   8984 S   0.0   0.2   0:01.61 systemd-resolve
    602 systemd+  20   0   88452   6196   5496 S   0.0   0.1   0:00.84 systemd-timesyn
    610 root      20   0    8316   4816   1676 S   0.0   0.1   0:01.92 haveged
    635 root      20   0  240700   7868   6804 S   0.0   0.1   0:00.53 accounts-daemon
    641 avahi     20   0    7436   3528   3176 S   0.0   0.0   0:00.28 avahi-daemon
    643 root      20   0    9484   2900   2688 S   0.0   0.0   0:00.02 cron
    645 message+  20   0    9884   6284   4244 S   0.0   0.1   0:09.43 dbus-daemon
    647 root      20   0  263528  19052  16316 S   0.0   0.2   0:02.15 NetworkManager
    652 root      20   0  231720   6536   5636 S   0.0   0.1   0:01.18 iio-sensor-prox
    653 root      20   0   82912   4204   3852 S   0.0   0.1   0:00.38 irqbalance
    654 root      20   0   33848  19384  10600 S   0.0   0.2   0:00.69 networkd-dispat
    658 root      20   0  237500   9804   6936 S   0.0   0.1   0:04.41 polkitd
    660 syslog    20   0  221216   4760   3940 S   0.0   0.1   0:00.44 rsyslogd
    669 root      20   0   11992   6208   4804 S   0.0   0.1   0:00.19 smartd
    671 root      20   0 1072124  29012  15600 S   0.0   0.4   0:07.88 snapd
    678 root      20   0  505456   7624   6688 S   0.0   0.1   0:01.52 systemd-logind
    679 root      20   0  127792   9252   8416 S   0.0   0.1   0:00.50 thermald
    680 root      20   0  393988  13256  10584 S   0.0   0.2   0:03.09 udisksd
    681 root      20   0   14872   8488   7680 S   0.0   0.1   0:00.14 wpa_supplicant
    696 avahi     20   0    7252    352      0 S   0.0   0.0   0:00.00 avahi-daemon
    727 root      20   0   72156  13732  11544 S   0.0   0.2   0:00.15 cupsd
    739 root      20   0  316720  11276   9708 S   0.0   0.1   0:00.46 ModemManager
    751 lp        20   0   16552   6832   5992 S   0.0   0.1   0:00.02 dbus
    765 root      20   0  179212  12928  11244 S   0.0   0.2   0:00.26 cups-browsed
    767 root      20   0  111640  21628  13208 S   0.0   0.3   0:00.59 unattended-upgr
    770 root      20   0  139564  16420  15036 S   0.0   0.2   0:00.15 sddm
    880 rtkit     21   1  153848   2992   2740 S   0.0   0.0   0:00.15 rtkit-daemon
    941 root      20   0  249908   8868   7612 S   0.0   0.1   0:01.23 upowerd
    964 whoopsie  20   0  252312  14548  12744 S   0.0   0.2   0:00.22 whoopsie
    965 kernoops  20   0   13528    472      0 S   0.0   0.0   0:00.00 kerneloops
    967 kernoops  20   0   13528    472      0 S   0.0   0.0   0:00.00 kerneloops
    971 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 kworker/u17:1
    975 root      20   0   57424  15688  14188 S   0.0   0.2   0:00.49 sddm-helper
    977 bradley   20   0   16888  10468   7472 S   0.0   0.1   0:01.96 systemd
    978 bradley   20   0  167836   3708     24 S   0.0   0.0   0:00.00 (sd-pam)
    984 bradley    9 -11   90952   6016   4908 S   0.0   0.1   0:00.30 pipewire
    985 bradley    9 -11   82976   5924   4908 S   0.0   0.1   0:00.25 pipewire-media-
    986 bradley    9 -11 1147484  20388  15512 S   0.0   0.3   0:00.75 pulseaudio
    991 bradley   20   0    8812   5184   4184 S   0.0   0.1   0:05.03 dbus-daemon
    993 bradley   20   0  281920  43916  38656 S   0.0   0.5   0:01.73 kwalletd5
    994 bradley   20   0  145564  18768  16784 S   0.0   0.2   0:00.43 startplasma-x11
   1045 bradley   20   0  245668   9500   8440 S   0.0   0.1   0:00.05 gsettings-helpe
   1121 bradley   20   0    5964    452      0 S   0.0   0.0   0:00.00 ssh-agent
   1217 root      20   0   89488  25592  22352 S   0.0   0.3   0:00.43 smbd
   1219 root      20   0   87196  10356   7400 S   0.0   0.1   0:00.00 smbd-notifyd
   1220 root      20   0   87188   7988   5032 S   0.0   0.1   0:00.00 cleanupd
   1223 root      20   0   89496  11616   8372 S   0.0   0.1   0:00.03 lpqd
   1228 bradley   20   0    2424     96      0 S   0.0   0.0   0:00.00 start_kdeinit
   1229 bradley   20   0  113924  26428  22608 S   0.0   0.3   0:00.28 kdeinit5
   1230 bradley   20   0  279868  40968  36108 S   0.0   0.5   0:01.00 klauncher
   1245 bradley   20   0 1128864 208716 154976 S   0.0   2.6   0:14.87 kded5
   1250 bradley   20   0  544096  34460  30324 S   0.0   0.4   0:01.59 kactivitymanage
   1260 bradley   20   0  281444  42812  36592 S   0.0   0.5   0:03.90 kglobalaccel5
   1270 bradley   20   0  157408   5796   5288 S   0.0   0.1   0:00.10 dconf-service
   1276 bradley   20   0    7960   3992   3640 S   0.0   0.0   0:00.07 xsettingsd
   1281 bradley   20   0  284744  47628  41576 S   0.0   0.6   0:02.38 ksmserver
   1302 bradley   20   0  430892  45400  39984 S   0.0   0.6   0:02.18 polkit-kde-auth
   1305 bradley   20   0  479796  40364  35812 S   0.0   0.5   0:03.06 org_kde_powerde
   1311 bradley   20   0  230920  23128  20528 S   0.0   0.3   0:00.85 xembedsniproxy
   1313 bradley   20   0  286496  44712  39328 S   0.0   0.6   0:02.10 kaccess
   1322 bradley   20   0  232240  24644  21968 S   0.0   0.3   0:01.02 gmenudbusmenupr
   1328 bradley   20   0  368044  49272  43264 S   0.0   0.6   0:03.13 DiscoverNotifie
   1335 bradley   20   0  717676  64800  54692 S   0.0   0.8   0:04.90 kdeconnectd
   1384 root      20   0  372620  50320  19516 S   0.0   0.6   0:17.79 packagekitd
   1399 bradley   20   0  306720   7292   6624 S   0.0   0.1   0:00.26 at-spi-bus-laun
   1415 bradley   20   0    8120   4024   3648 S   0.0   0.1   0:00.10 dbus-daemon
   1425 bradley   20   0  236868   5436   4996 S   0.0   0.1   0:00.11 agent
   1452 bradley   20   0  223936  21196  18604 S   0.0   0.3   0:01.19 kscreen_backend
   1456 bradley   20   0   45716   6904   6244 S   0.0   0.1   0:00.10 obexd
   1506 bradley   20   0   86016  19516  17732 S   0.0   0.2   0:00.09 kioslave5
   1508 bradley   20   0   86016  19392  17604 S   0.0   0.2   0:00.09 kioslave5
   1515 root       0 -20       0      0      0 I   0.0   0.0   0:00.00 cfg80211
   1526 root      20   0       0      0      0 S   0.0   0.0   0:00.48 RTW_CMD_THREAD
   1673 bradley   20   0 8847204 185852  88588 S   0.0   2.3   0:59.38 WebExtensions
   1727 bradley   20   0  283320  45272  39964 S   0.0   0.6   0:01.73 plasma-browser-
   1762 bradley   20   0 2465972 128108  93716 S   0.0   1.6   0:14.07 Privileged Cont
   1802 bradley   20   0 2655672 175900 106268 S   0.0   2.2   0:48.79 Web Content
   1901 root      20   0       0      0      0 I   0.0   0.0   0:00.45 kworker/2:1-events
   1927 root      20   0       0      0      0 I   0.0   0.0   0:00.67 kworker/1:1-mm_percpu_wq
   2094 root      20   0       0      0      0 I   0.0   0.0   0:00.16 kworker/u16:0-i915
   2636 bradley   20   0 2413592  76392  64256 S   0.0   0.9   0:00.89 Web Content
   2667 bradley   20   0  225984  40000  32344 S   0.0   0.5   0:00.60 RDD Process
   2687 root      20   0       0      0      0 I   0.0   0.0   0:00.54 kworker/0:0-events
   2689 root      20   0       0      0      0 I   0.0   0.0   0:00.81 kworker/3:0-events
   2694 root      20   0       0      0      0 I   0.0   0.0   0:00.58 kworker/2:2-mm_percpu_wq
   2700 root      20   0       0      0      0 I   0.0   0.0   0:02.52 kworker/1:0-events
   2757 bradley   20   0 1019860 106124  85828 S   0.0   1.3   0:06.75 konsole
   2769 bradley   20   0   10844   5028   3556 S   0.0   0.1   0:00.13 bash
   2794 root      20   0       0      0      0 I   0.0   0.0   0:00.30 kworker/0:1-events
   2805 root      20   0       0      0      0 I   0.0   0.0   0:00.17 kworker/2:0-events
   2806 root      20   0       0      0      0 I   0.0   0.0   0:00.00 kworker/3:1-events
   2807 root      20   0       0      0      0 I   0.0   0.0   0:00.84 kworker/1:2-events


```

---

### Post by bradleypariah on 2021-09-21
> **TheFu said:**
> So ... the passmarks on both these systems are  pretty low for Core i7 systems.  I have a $50 Pentium desktop CPU -  G3258 - from 2015 that is between these in performance.

i7-5500U - 2726
i7-L640 - 1680
G3258 - 2057

A $305 laptop with a Core i5-8258U has 5944 passmarks.  Just sayin'.   Core i7s from the last 2-3 yrs should be in the 16K passmark area.
BTW, the passmark guys routinely rework their numbers so any comparisons  are only valid within the same search.  Last year, the G3258 passmarks  was over 3600 - as newer CPUs get faster, they tweak the benchmark and  all older CPUs ratings are shifted down. I remember a Celeron 2995U in a  chromebook was around 1470 passmarks. Just checked that now and it  lists around 800.  I ran virtual machines on that chromebook!  It worked  fine - except the RAM limitations.

I was watching a  YouTube video today where a guy installed Manjaro on a 2012 MacBook Pro,  and the exact second he clicked the Firefox icon, the application  window was open.  For me, when I click the Firefox icon, nothing happens  for at least five seconds.  My home screen doesn't load for another  15-20.  I'm not wanting to edit video on this thing or play Fallout 4 on  max settings, it just seems like everything takes longer than it's  supposed to.

> **TheFu said:**
> S
All sorts of things go into what makes a system fast or slow.  A failing  disk or corrupted file system or slow DNS can impact perceived  performance.  It is unlikely we will be able to see things by posting  commands on a forum.  I know the forum moderation team has been working  on a "system information" script to help troubleshoot all things Ubuntu,  but it isn't quite ready.  You could run **inxi -Fxxxxz** and post that output as a start.  
```
[FONT=monospace][COLOR=#54ff54]**bradley@Flex-3-1570**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ inxi -Fxxxxz [/COLOR]
[COLOR=#5454ff]**System:    Kernel:**[/COLOR][COLOR=#000000] 5.11.0-34-generic x86_64 [/COLOR][COLOR=#5454ff]**bits:**[/COLOR][COLOR=#000000] 64 [/COLOR][COLOR=#5454ff]**compiler:**[/COLOR][COLOR=#000000] gcc [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] 10.2.1 [/COLOR][COLOR=#5454ff]**Desktop:**[/COLOR][COLOR=#000000] KDE Plasma 5.22.5 [/COLOR][COLOR=#5454ff]**tk:**[/COLOR][COLOR=#000000] Qt 5.15.2  [/COLOR]
           [COLOR=#5454ff]**wm:**[/COLOR][COLOR=#000000] kwin_x11 [/COLOR][COLOR=#5454ff]**dm:**[/COLOR][COLOR=#000000] SDDM [/COLOR][COLOR=#5454ff]**Distro:**[/COLOR][COLOR=#000000] Ubuntu 21.04 (Hirsute Hippo)  [/COLOR]
[COLOR=#5454ff]**Machine:   Type:**[/COLOR][COLOR=#000000] Laptop [/COLOR][COLOR=#5454ff]**System:**[/COLOR][COLOR=#000000] LENOVO [/COLOR][COLOR=#5454ff]**product:**[/COLOR][COLOR=#000000] 80JM [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] Flex 3-1570 [/COLOR][COLOR=#5454ff]**serial:**[/COLOR][COLOR=#000000] <filter> [/COLOR][COLOR=#5454ff]**Chassis:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5454ff]**type:**[/COLOR][COLOR=#000000] 10 [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] Flex 3-1570  [/COLOR]
           [COLOR=#5454ff]**serial:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
           [COLOR=#5454ff]**Mobo:**[/COLOR][COLOR=#000000] LENOVO [/COLOR][COLOR=#5454ff]**model:**[/COLOR][COLOR=#000000] Flex 3-1570 [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] 31900058 WIN [/COLOR][COLOR=#5454ff]**serial:**[/COLOR][COLOR=#000000] <filter> [/COLOR][COLOR=#5454ff]**UEFI:**[/COLOR][COLOR=#000000] Lenovo [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] BDCN28WW [/COLOR][COLOR=#5454ff]**date:**[/COLOR][COLOR=#000000] 03/10/2015  [/COLOR]
[COLOR=#5454ff]**Battery:   ID-1:**[/COLOR][COLOR=#000000] BAT0 [/COLOR][COLOR=#5454ff]**charge:**[/COLOR][COLOR=#000000] 7.6 Wh [/COLOR][COLOR=#5454ff]**condition:**[/COLOR][COLOR=#000000] 30.2/45.0 Wh (67%) [/COLOR][COLOR=#5454ff]**volts:**[/COLOR][COLOR=#000000] 11.8/11.1 [/COLOR][COLOR=#5454ff]**model:**[/COLOR][COLOR=#000000] SMP L14M3P21 [/COLOR][COLOR=#5454ff]**type:**[/COLOR][COLOR=#000000] Li-poly  [/COLOR]
           [COLOR=#5454ff]**serial:**[/COLOR][COLOR=#000000] <filter> [/COLOR][COLOR=#5454ff]**status:**[/COLOR][COLOR=#000000] Charging  [/COLOR]
[COLOR=#5454ff]**CPU:       Info:**[/COLOR][COLOR=#000000] Dual Core [/COLOR][COLOR=#5454ff]**model:**[/COLOR][COLOR=#000000] Intel Core i7-5500U [/COLOR][COLOR=#5454ff]**bits:**[/COLOR][COLOR=#000000] 64 [/COLOR][COLOR=#5454ff]**type:**[/COLOR][COLOR=#000000] MT MCP [/COLOR][COLOR=#5454ff]**arch:**[/COLOR][COLOR=#000000] Broadwell [/COLOR][COLOR=#5454ff]**rev:**[/COLOR][COLOR=#000000] 4 [/COLOR][COLOR=#5454ff]**L2 cache:**[/COLOR][COLOR=#000000] 4 MiB  [/COLOR]
           [COLOR=#5454ff]**flags:**[/COLOR][COLOR=#000000] avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 [/COLOR][COLOR=#5454ff]**bogomips:**[/COLOR][COLOR=#000000] 19154  [/COLOR]
           [COLOR=#5454ff]**Speed:**[/COLOR][COLOR=#000000] 499 MHz [/COLOR][COLOR=#5454ff]**min/max:**[/COLOR][COLOR=#000000] 500/3000 MHz [/COLOR][COLOR=#5454ff]**Core speeds (MHz):**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5454ff]**1:**[/COLOR][COLOR=#000000] 499 [/COLOR][COLOR=#5454ff]**2:**[/COLOR][COLOR=#000000] 499 [/COLOR][COLOR=#5454ff]**3:**[/COLOR][COLOR=#000000] 499 [/COLOR][COLOR=#5454ff]**4:**[/COLOR][COLOR=#000000] 499  [/COLOR]
[COLOR=#5454ff]**Graphics:  Device-1:**[/COLOR][COLOR=#000000] Intel HD Graphics 5500 [/COLOR][COLOR=#5454ff]**vendor:**[/COLOR][COLOR=#000000] Lenovo [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] i915 [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR][COLOR=#5454ff]**bus ID:**[/COLOR][COLOR=#000000] 00:02.0 [/COLOR][COLOR=#5454ff]**chip ID:**[/COLOR][COLOR=#000000] 8086:1616  [/COLOR]
           [COLOR=#5454ff]**class ID:**[/COLOR][COLOR=#000000] 0300  [/COLOR]
           [COLOR=#5454ff]**Device-2:**[/COLOR][COLOR=#000000] Chicony Lenovo EasyCamera [/COLOR][COLOR=#5454ff]**type:**[/COLOR][COLOR=#000000] USB [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] uvcvideo [/COLOR][COLOR=#5454ff]**bus ID:**[/COLOR][COLOR=#000000] 2-4:2 [/COLOR][COLOR=#5454ff]**chip ID:**[/COLOR][COLOR=#000000] 04f2:b50f [/COLOR][COLOR=#5454ff]**class ID:**[/COLOR][COLOR=#000000] 0e02  [/COLOR]
           [COLOR=#5454ff]**serial:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
           [COLOR=#5454ff]**Display:**[/COLOR][COLOR=#000000] x11 [/COLOR][COLOR=#5454ff]**server:**[/COLOR][COLOR=#000000] X.Org 1.20.11 [/COLOR][COLOR=#5454ff]**compositor:**[/COLOR][COLOR=#000000] kwin_x11 [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5454ff]**loaded:**[/COLOR][COLOR=#000000] modesetting [/COLOR][COLOR=#5454ff]**unloaded:**[/COLOR][COLOR=#000000] fbdev,vesa  [/COLOR]
           [COLOR=#5454ff]**resolution:**[/COLOR][COLOR=#000000] 1920x1080~60Hz [/COLOR][COLOR=#5454ff]**s-dpi:**[/COLOR][COLOR=#000000] 96  [/COLOR]
           [COLOR=#5454ff]**OpenGL:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5454ff]**renderer:**[/COLOR][COLOR=#000000] Mesa Intel HD Graphics 5500 (BDW GT2) [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] 4.6 Mesa 21.0.3 [/COLOR][COLOR=#5454ff]**direct render:**[/COLOR][COLOR=#000000] Yes  [/COLOR]
[COLOR=#5454ff]**Audio:     Device-1:**[/COLOR][COLOR=#000000] Intel Broadwell-U Audio [/COLOR][COLOR=#5454ff]**vendor:**[/COLOR][COLOR=#000000] Lenovo [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR][COLOR=#5454ff]**bus ID:**[/COLOR][COLOR=#000000] 00:03.0  [/COLOR]
           [COLOR=#5454ff]**chip ID:**[/COLOR][COLOR=#000000] 8086:160c [/COLOR][COLOR=#5454ff]**class ID:**[/COLOR][COLOR=#000000] 0403  [/COLOR]
           [COLOR=#5454ff]**Device-2:**[/COLOR][COLOR=#000000] Intel Wildcat Point-LP High Definition Audio [/COLOR][COLOR=#5454ff]**vendor:**[/COLOR][COLOR=#000000] Lenovo [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] snd_hda_intel [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] kernel  [/COLOR]
           [COLOR=#5454ff]**bus ID:**[/COLOR][COLOR=#000000] 00:1b.0 [/COLOR][COLOR=#5454ff]**chip ID:**[/COLOR][COLOR=#000000] 8086:9ca0 [/COLOR][COLOR=#5454ff]**class ID:**[/COLOR][COLOR=#000000] 0403  [/COLOR]
           [COLOR=#5454ff]**Sound Server:**[/COLOR][COLOR=#000000] ALSA [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] k5.11.0-34-generic  [/COLOR]
[COLOR=#5454ff]**Network:   Device-1:**[/COLOR][COLOR=#000000] Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet [/COLOR][COLOR=#5454ff]**vendor:**[/COLOR][COLOR=#000000] Lenovo [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] r8169 [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] kernel  [/COLOR]
           [COLOR=#5454ff]**port:**[/COLOR][COLOR=#000000] 3000 [/COLOR][COLOR=#5454ff]**bus ID:**[/COLOR][COLOR=#000000] 03:00.0 [/COLOR][COLOR=#5454ff]**chip ID:**[/COLOR][COLOR=#000000] 10ec:8168 [/COLOR][COLOR=#5454ff]**class ID:**[/COLOR][COLOR=#000000] 0200  [/COLOR]
           [COLOR=#5454ff]**IF:**[/COLOR][COLOR=#000000] enp3s0 [/COLOR][COLOR=#5454ff]**state:**[/COLOR][COLOR=#000000] down [/COLOR][COLOR=#5454ff]**mac:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
           [COLOR=#5454ff]**Device-2:**[/COLOR][COLOR=#000000] Realtek RTL8188EUS 802.11n Wireless Network Adapter [/COLOR][COLOR=#5454ff]**type:**[/COLOR][COLOR=#000000] USB [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] r8188eu [/COLOR][COLOR=#5454ff]**bus ID:**[/COLOR][COLOR=#000000] 2-5:4  [/COLOR]
           [COLOR=#5454ff]**chip ID:**[/COLOR][COLOR=#000000] 0bda:8179 [/COLOR][COLOR=#5454ff]**class ID:**[/COLOR][COLOR=#000000] 0000 [/COLOR][COLOR=#5454ff]**serial:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
           [COLOR=#5454ff]**IF:**[/COLOR][COLOR=#000000] wlxd0374577aed4 [/COLOR][COLOR=#5454ff]**state:**[/COLOR][COLOR=#000000] up [/COLOR][COLOR=#5454ff]**mac:**[/COLOR][COLOR=#000000] <filter>  [/COLOR]
[COLOR=#5454ff]**Drives:    Local Storage:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5454ff]**total:**[/COLOR][COLOR=#000000] 119.24 GiB [/COLOR][COLOR=#5454ff]**used:**[/COLOR][COLOR=#000000] 42.36 GiB (35.5%)  [/COLOR]
           [COLOR=#5454ff]**ID-1:**[/COLOR][COLOR=#000000] /dev/sda [/COLOR][COLOR=#5454ff]**vendor:**[/COLOR][COLOR=#000000] Samsung [/COLOR][COLOR=#5454ff]**model:**[/COLOR][COLOR=#000000] MZ7LN128HCHP-000L1 [/COLOR][COLOR=#5454ff]**size:**[/COLOR][COLOR=#000000] 119.24 GiB [/COLOR][COLOR=#5454ff]**speed:**[/COLOR][COLOR=#000000] 6.0 Gb/s [/COLOR][COLOR=#5454ff]**rotation:**[/COLOR][COLOR=#000000] SSD  [/COLOR]
           [COLOR=#5454ff]**serial:**[/COLOR][COLOR=#000000] <filter> [/COLOR][COLOR=#5454ff]**rev:**[/COLOR][COLOR=#000000] 3L0Q [/COLOR][COLOR=#5454ff]**scheme:**[/COLOR][COLOR=#000000] GPT  [/COLOR]
[COLOR=#5454ff]**Partition: ID-1:**[/COLOR][COLOR=#000000] / [/COLOR][COLOR=#5454ff]**size:**[/COLOR][COLOR=#000000] 34.53 GiB [/COLOR][COLOR=#5454ff]**used:**[/COLOR][COLOR=#000000] 19.23 GiB (55.7%) [/COLOR][COLOR=#5454ff]**fs:**[/COLOR][COLOR=#000000] ext4 [/COLOR][COLOR=#5454ff]**dev:**[/COLOR][COLOR=#000000] /dev/sda2  [/COLOR]
           [COLOR=#5454ff]**ID-2:**[/COLOR][COLOR=#000000] /boot/efi [/COLOR][COLOR=#5454ff]**size:**[/COLOR][COLOR=#000000] 92.5 MiB [/COLOR][COLOR=#5454ff]**used:**[/COLOR][COLOR=#000000] 5.2 MiB (5.6%) [/COLOR][COLOR=#5454ff]**fs:**[/COLOR][COLOR=#000000] vfat [/COLOR][COLOR=#5454ff]**dev:**[/COLOR][COLOR=#000000] /dev/sda1  [/COLOR]
           [COLOR=#5454ff]**ID-3:**[/COLOR][COLOR=#000000] /home [/COLOR][COLOR=#5454ff]**size:**[/COLOR][COLOR=#000000] 72.84 GiB [/COLOR][COLOR=#5454ff]**used:**[/COLOR][COLOR=#000000] 23.12 GiB (31.7%) [/COLOR][COLOR=#5454ff]**fs:**[/COLOR][COLOR=#000000] ext4 [/COLOR][COLOR=#5454ff]**dev:**[/COLOR][COLOR=#000000] /dev/sda4  [/COLOR]
[COLOR=#5454ff]**Swap:      ID-1:**[/COLOR][COLOR=#000000] swap-1 [/COLOR][COLOR=#5454ff]**type:**[/COLOR][COLOR=#000000] partition [/COLOR][COLOR=#5454ff]**size:**[/COLOR][COLOR=#000000] 9.31 GiB [/COLOR][COLOR=#5454ff]**used:**[/COLOR][COLOR=#000000] 0 KiB (0.0%) [/COLOR][COLOR=#5454ff]**priority:**[/COLOR][COLOR=#000000] -2 [/COLOR][COLOR=#5454ff]**dev:**[/COLOR][COLOR=#000000] /dev/sda3  [/COLOR]
[COLOR=#5454ff]**Sensors:   System Temperatures:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5454ff]**cpu:**[/COLOR][COLOR=#000000] 39.0 C [/COLOR][COLOR=#5454ff]**mobo:**[/COLOR][COLOR=#000000] 38.0 C  [/COLOR]
           [COLOR=#5454ff]**Fan Speeds (RPM):**[/COLOR][COLOR=#000000] N/A  [/COLOR]
[COLOR=#5454ff]**Info:      Processes:**[/COLOR][COLOR=#000000] 208 [/COLOR][COLOR=#5454ff]**Uptime:**[/COLOR][COLOR=#000000] 33m [/COLOR][COLOR=#5454ff]**wakeups:**[/COLOR][COLOR=#000000] 2 [/COLOR][COLOR=#5454ff]**Memory:**[/COLOR][COLOR=#000000] 7.67 GiB [/COLOR][COLOR=#5454ff]**used:**[/COLOR][COLOR=#000000] 1.97 GiB (25.7%) [/COLOR][COLOR=#5454ff]**Init:**[/COLOR][COLOR=#000000] systemd [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] 247 [/COLOR][COLOR=#5454ff]**runlevel:**[/COLOR][COLOR=#000000] 5  [/COLOR]
           [COLOR=#5454ff]**Compilers:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5454ff]**gcc:**[/COLOR][COLOR=#000000] 10.3.0 [/COLOR][COLOR=#5454ff]**alt:**[/COLOR][COLOR=#000000] 10/9 [/COLOR][COLOR=#5454ff]**Packages:**[/COLOR][COLOR=#000000] 2373 [/COLOR][COLOR=#5454ff]**apt:**[/COLOR][COLOR=#000000] 2363 [/COLOR][COLOR=#5454ff]**snap:**[/COLOR][COLOR=#000000] 10 [/COLOR][COLOR=#5454ff]**Shell:**[/COLOR][COLOR=#000000] Bash [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] 5.1.4 [/COLOR][COLOR=#5454ff]**running in:**[/COLOR][COLOR=#000000] konsole  [/COLOR]
           [COLOR=#5454ff]**inxi:**[/COLOR][COLOR=#000000] 3.3.01 [/COLOR]
[/FONT]
```
> **TheFu said:**
>  It won't be able to see any hardware issues.  Only you can see that.   Check the system log files for errors and warnings.  I'd use 
**sudo    egrep    -i      'erro|warn'      /var/log/*log**
and look over that output.  There really should only be a few lines. If  there are more, redirect the output to a file and use your favorite  editor to look more closely.  The **journalctl** command can do some searches for system logs too.

```
[FONT=monospace][COLOR=#54ff54]**bradley@Flex-3-1570**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo egrep -i 'erro|warn' /var/log/*log [/COLOR]
[sudo] password for bradley:  
/var/log/auth.log:Sep 21 16:06:47 Flex-3-1570 sudo:  bradley : TTY=pts/1 ; PWD=/home/bradley ; USER=root ; COMMAND=/usr/bin/eg
rep -i erro|warn /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var
/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/gpu-manager.log /var/log/gpu-manager-switch.log /var/log/kern.
log /var/log/lastlog /var/log/prime-offload.log /var/log/prime-supported.log /var/log/sddm.log /var/log/syslog /var/log/ubuntu
-advantage.log /var/log/Xorg.0.log 
/var/log/auth.log:Sep 21 16:25:22 Flex-3-1570 sudo:  bradley : TTY=pts/1 ; PWD=/home/bradley ; USER=root ; COMMAND=/usr/bin/eg
rep -i erro|warn /var/log/alternatives.log /var/log/apport.log /var/log/auth.log /var/log/boot.log /var/log/bootstrap.log /var
/log/dpkg.log /var/log/faillog /var/log/fontconfig.log /var/log/gpu-manager.log /var/log/gpu-manager-switch.log /var/log/kern.
log /var/log/lastlog /var/log/prime-offload.log /var/log/prime-supported.log /var/log/sddm.log /var/log/syslog /var/log/ubuntu
-advantage.log /var/log/Xorg.0.log 
/var/log/bootstrap.log:2020-04-01 12:22:12 URL:http://ftpmaster.internal/ubuntu/pool/main/libg/libgpg-error/libgpg-error0_1.37
-1_amd64.deb [58004/58004] -> "/build/chroot//var/cache/apt/archives/partial/libgpg-error0_1.37-1_amd64.deb" [1] 
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 5 package 'dpkg': 
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 5 package 'dpkg': 
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 24 package 'dpkg': 
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 24 package 'dpkg': 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 60 package 'dpkg': 
/var/log/bootstrap.log:dpkg: warning: parsing file '/var/lib/dpkg/status' near line 60 package 'dpkg': 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:Selecting previously unselected package libgpg-error0:amd64. 
/var/log/bootstrap.log:Preparing to unpack .../libgpg-error0_1.37-1_amd64.deb ... 
/var/log/bootstrap.log:Unpacking libgpg-error0:amd64 (1.37-1) ... 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:dpkg: warning: ignoring pre-dependency problem! 
/var/log/bootstrap.log:Setting up libgpg-error0:amd64 (1.37-1) ... 
/var/log/bootstrap.log:/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in b
inary mode, the default buffer size will be used 
/var/log/bootstrap.log:/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in b
inary mode, the default buffer size will be used 
/var/log/bootstrap.log:/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in b
inary mode, the default buffer size will be used 
/var/log/bootstrap.log:/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in b
inary mode, the default buffer size will be used 
/var/log/bootstrap.log:/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in b
inary mode, the default buffer size will be used 
/var/log/bootstrap.log:/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in b
inary mode, the default buffer size will be used 
/var/log/bootstrap.log:/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in b
inary mode, the default buffer size will be used 
/var/log/bootstrap.log:/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in b
inary mode, the default buffer size will be used 
/var/log/bootstrap.log:/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in b
inary mode, the default buffer size will be used 
/var/log/bootstrap.log:/usr/lib/python3.8/subprocess.py:838: RuntimeWarning: line buffering (buffering=1) isn't supported in b
inary mode, the default buffer size will be used 
/var/log/kern.log:Sep 21 15:50:47 Flex-3-1570 kernel: [    1.180739] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM 
/var/log/kern.log:Sep 21 15:50:47 Flex-3-1570 kernel: [    2.737852] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI
0.LPCB.HEC.ECRD], AE_NOT_FOUND (20201113/psargs-330) 
/var/log/kern.log:Sep 21 15:50:47 Flex-3-1570 kernel: [    2.737920] ACPI Error: Aborting method \_TZ.TZ00._TMP due to previou
s error (AE_NOT_FOUND) (20201113/psparse-529) 
/var/log/kern.log:Sep 21 15:50:47 Flex-3-1570 kernel: [    2.738952] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI
0.LPCB.HEC.ECRD], AE_NOT_FOUND (20201113/psargs-330) 
/var/log/kern.log:Sep 21 15:50:47 Flex-3-1570 kernel: [    2.739003] ACPI Error: Aborting method \_TZ.TZ00._TMP due to previou
s error (AE_NOT_FOUND) (20201113/psparse-529) 
/var/log/kern.log:Sep 21 15:50:47 Flex-3-1570 kernel: [    2.739452] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI
0.LPCB.HEC.ECRD], AE_NOT_FOUND (20201113/psargs-330) 
/var/log/kern.log:Sep 21 15:50:47 Flex-3-1570 kernel: [    2.739498] ACPI Error: Aborting method \_TZ.TZ01._TMP due to previou
s error (AE_NOT_FOUND) (20201113/psparse-529) 
/var/log/kern.log:Sep 21 15:50:47 Flex-3-1570 kernel: [    2.740188] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI
0.LPCB.HEC.ECRD], AE_NOT_FOUND (20201113/psargs-330) 
/var/log/kern.log:Sep 21 15:50:47 Flex-3-1570 kernel: [    2.740233] ACPI Error: Aborting method \_TZ.TZ01._TMP due to previou
s error (AE_NOT_FOUND) (20201113/psparse-529) 
/var/log/kern.log:Sep 21 15:50:47 Flex-3-1570 kernel: [    3.029799] RAS: Correctable Errors collector initialized. 
/var/log/kern.log:Sep 21 15:50:47 Flex-3-1570 kernel: [   13.984893] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro. Quot
a mode: none. 
/var/log/kern.log:Sep 21 15:55:21 Flex-3-1570 kernel: [  297.972870] r8188eu: module is from the staging directory, the qualit
y is unknown, you have been warned. 
/var/log/syslog:Sep 21 15:19:53 Flex-3-1570 snapd[684]: stateengine.go:150: state ensure error: persistent network error: Post
 https://api.snapcraft.io/v2/snaps/refresh: dial tcp: lookup api.snapcraft.io: Temporary failure in name resolution 
/var/log/syslog:Sep 21 15:20:26 Flex-3-1570 NetworkManager[655]:  <warn>  [1632262826.9811] wifi-wext: error getting interface 
name for ifindex 3, operation 'get-mode': No such device or address (6) 
/var/log/syslog:Sep 21 15:20:27 Flex-3-1570 NetworkManager[655]:  <warn>  [1632262827.0732] dns-sd-resolved[51f9ff03ac7d2636]: 
send-updates SetLinkDomains@3 failed: GDBus.Error:org.freedesktop.resolve1.NoSuchLink: Link 3 not known 
/var/log/syslog:Sep 21 15:37:59 Flex-3-1570 fwupd[4145]: ERROR:esys:src/tss2-esys/esys_context.c:69:Esys_Initialize() Initiali
ze default tcti. ErrorCode (0x000a000a) 
/var/log/syslog:Sep 21 15:41:14 Flex-3-1570 org.kde.LogoutPrompt[11313]: file:///usr/share/plasma/look-and-feel/org.kde.breeze
.desktop/contents/components/UserDelegate.qml:35: ReferenceError: model is not defined 
/var/log/syslog:Sep 21 15:41:29 Flex-3-1570 org.kde.kdeconnect[11466]: ICE default IO error handler doing an exit(), pid = 114
66, errno = 11 
/var/log/syslog:Sep 21 15:41:29 Flex-3-1570 sddm[792]: Authentication error: "Process crashed" 
/var/log/syslog:Sep 21 15:41:29 Flex-3-1570 kactivitymanagerd[1258]: The X11 connection broke (error 1). Did the X11 server di
e? 
/var/log/syslog:Sep 21 15:41:29 Flex-3-1570 kglobalaccel5[1266]: The X11 connection broke (error 1). Did the X11 server die? 
/var/log/syslog:Sep 21 15:41:29 Flex-3-1570 sddm[792]: Authentication error: "Process crashed" 
/var/log/syslog:Sep 21 15:41:29 Flex-3-1570 org.kde.KScreen[1458]: The X11 connection broke (error 1). Did the X11 server die? 
/var/log/syslog:Sep 21 15:50:47 Flex-3-1570 systemd[1]: Condition check resulted in Process error reports when automatic repor
ting is enabled (file watch) being skipped. 
/var/log/syslog:Sep 21 15:50:47 Flex-3-1570 kernel: [    1.180739] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM 
/var/log/syslog:Sep 21 15:50:47 Flex-3-1570 kernel: [    2.737852] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.
LPCB.HEC.ECRD], AE_NOT_FOUND (20201113/psargs-330) 
/var/log/syslog:Sep 21 15:50:47 Flex-3-1570 kernel: [    2.737920] ACPI Error: Aborting method \_TZ.TZ00._TMP due to previous 
error (AE_NOT_FOUND) (20201113/psparse-529) 
/var/log/syslog:Sep 21 15:50:47 Flex-3-1570 kernel: [    2.738952] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.
LPCB.HEC.ECRD], AE_NOT_FOUND (20201113/psargs-330) 
/var/log/syslog:Sep 21 15:50:47 Flex-3-1570 kernel: [    2.739003] ACPI Error: Aborting method \_TZ.TZ00._TMP due to previous 
error (AE_NOT_FOUND) (20201113/psparse-529) 
/var/log/syslog:Sep 21 15:50:47 Flex-3-1570 kernel: [    2.739452] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.
LPCB.HEC.ECRD], AE_NOT_FOUND (20201113/psargs-330) 
/var/log/syslog:Sep 21 15:50:47 Flex-3-1570 kernel: [    2.739498] ACPI Error: Aborting method \_TZ.TZ01._TMP due to previous 
error (AE_NOT_FOUND) (20201113/psparse-529) 
/var/log/syslog:Sep 21 15:50:47 Flex-3-1570 kernel: [    2.740188] ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.
LPCB.HEC.ECRD], AE_NOT_FOUND (20201113/psargs-330) 
/var/log/syslog:Sep 21 15:50:47 Flex-3-1570 kernel: [    2.740233] ACPI Error: Aborting method \_TZ.TZ01._TMP due to previous 
error (AE_NOT_FOUND) (20201113/psparse-529) 
/var/log/syslog:Sep 21 15:50:47 Flex-3-1570 kernel: [    3.029799] RAS: Correctable Errors collector initialized. 
/var/log/syslog:Sep 21 15:50:47 Flex-3-1570 kernel: [   13.984893] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro. Quota 
mode: none. 
/var/log/syslog:Sep 21 15:50:48 Flex-3-1570 networkd-dispatcher[786]: WARNING: systemd-networkd is not running, output will be
 incomplete. 
/var/log/syslog:Sep 21 15:50:49 Flex-3-1570 NetworkManager[647]:  <warn>  [1632264649.3981] ifupdown: interfaces file /etc/netw
ork/interfaces doesn't exist 
/var/log/syslog:Sep 21 15:50:49 Flex-3-1570 NetworkManager[647]:  <warn>  [1632264649.8128] Error: failed to open /run/network/
ifstate 
/var/log/syslog:Sep 21 15:51:18 Flex-3-1570 pulseaudio[873]: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: D
id not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy 
blocked the reply, the reply timeout expired, or the network connection was broken. 
/var/log/syslog:Sep 21 15:51:25 Flex-3-1570 snapd[671]: stateengine.go:150: state ensure error: persistent network error: Get 
https://api.snapcraft.io/api/v1/snaps/sections: dial tcp: lookup api.snapcraft.io: Temporary failure in name resolution 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/Main.qml:4
20: TypeError: Cannot read property 'smallSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/Battery.qml:27: TypeError: Cannot read property 'smallSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/Main.qml:1
58: TypeError: Cannot read property 'gridUnit' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:102: TypeError: Cannot read property 'smallSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:39: TypeError: Cannot read property 'gridUnit' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:55: TypeError: Cannot read property 'smallSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:41: TypeError: Cannot read property 'largeSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:42: TypeError: Cannot read property 'smallSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:102: TypeError: Cannot read property 'smallSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:39: TypeError: Cannot read property 'gridUnit' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:55: TypeError: Cannot read property 'smallSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:41: TypeError: Cannot read property 'largeSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:42: TypeError: Cannot read property 'smallSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:102: TypeError: Cannot read property 'smallSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:39: TypeError: Cannot read property 'gridUnit' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:55: TypeError: Cannot read property 'smallSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:41: TypeError: Cannot read property 'largeSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:42: TypeError: Cannot read property 'smallSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:102: TypeError: Cannot read property 'smallSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:39: TypeError: Cannot read property 'gridUnit' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:55: TypeError: Cannot read property 'smallSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:41: TypeError: Cannot read property 'largeSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/ActionButton.qml:42: TypeError: Cannot read property 'smallSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/Login.qml:
120: TypeError: Cannot read property 'smallSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/Login.qml:
115: TypeError: Cannot read property 'smallSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/SessionManagementScreen.qml:84: TypeError: Cannot read property 'gridUnit' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/SessionManagementScreen.qml:114: TypeError: Cannot read property 'largeSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/SessionManagementScreen.qml:100: TypeError: Cannot read property 'gridUnit' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/SessionManagementScreen.qml:101: TypeError: Cannot read property 'gridUnit' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/SessionManagementScreen.qml:91: TypeError: Cannot read property 'gridUnit' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/UserList.qml:25: TypeError: Cannot read property 'gridUnit' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/UserList.qml:26: TypeError: Cannot read property 'gridUnit' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/UserDelegate.qml:103: TypeError: Cannot read property 'largeSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/UserDelegate.qml:44: TypeError: Cannot read property 'smallSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/UserDelegate.qml:69: TypeError: Cannot read property 'largeSpacing' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/UserDelegate.qml:95: TypeError: Cannot read property 'gridUnit' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/UserDelegate.qml:75: TypeError: Cannot read property 'longDuration' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/UserDelegate.qml:50: TypeError: Cannot read property 'longDuration' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/WallpaperFader.qml:159: TypeError: Cannot read property 'longDuration' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/components
/WallpaperFader.qml:153: TypeError: Cannot read property 'longDuration' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/Main.qml:2
39: TypeError: Cannot read property 'longDuration' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 sddm-greeter[877]: file:///usr/share/sddm/themes/Infinity-beauty-7-SDDM/Main.qml:4
25: TypeError: Cannot read property 'longDuration' of null 
/var/log/syslog:Sep 21 15:52:20 Flex-3-1570 systemd-xdg-autostart-generator[982]: Not generating service for XDG autostart app
-org.kde.latte\x2ddock-autostart.service, error parsing Exec= line: No such file or directory 
/var/log/syslog:Sep 21 15:52:25 Flex-3-1570 systemd-xdg-autostart-generator[1206]: Not generating service for XDG autostart ap
p-org.kde.latte\x2ddock-autostart.service, error parsing Exec= line: No such file or directory 
/var/log/syslog:Sep 21 15:52:47 Flex-3-1570 pulseaudio[986]: GetManagedObjects() failed: org.freedesktop.DBus.Error.NoReply: D
id not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy 
blocked the reply, the reply timeout expired, or the network connection was broken. 
/var/log/syslog:Sep 21 15:52:49 Flex-3-1570 org.kde.KScreen[1452]: kscreen.xcb.helper: Event Error:  147 
/var/log/syslog:Sep 21 15:55:21 Flex-3-1570 kernel: [  297.972870] r8188eu: module is from the staging directory, the quality 
is unknown, you have been warned. 
/var/log/syslog:Sep 21 15:55:27 Flex-3-1570 NetworkManager[647]:  <error> [1632264927.1572] wifi-wext: (wlxd0374577aed4): error
 setting powersave 1 
/var/log/Xorg.0.log:    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.


[/FONT]
```

---

### Post by bradleypariah on 2021-09-21
> **oldfred said:**
> Do you have latest firmware for both UEFI and SSD?
That can make a difference.

Looks like there's a BIOS/UEFI update for the Lenovo Flex 1570 available on their website, but it's in EXE format.  The instructions say to install it through Windows.... 
I'm thinking that running a BIOS update through Wine would be a bad idea, but I have no idea.
I guess I could wipe my laptop, install Windows, install the BIOS update, then wipe the laptop again, and finally put Kubuntu back.  :(

---

### Post by oldfred on 2021-09-21
Some Lenovo's now update thru Linux, but it looks like no Flex models.
Devices using LVFS for firmware updates
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)

Many UEFI can update directly from within UEFI if you download the update file & copy into a FAT32 partition, as that is the only file system UEFI can read. Many vendors offer just the update file, and the .exe for Windows users.

Do not know if something like this also works?
HP UEFI update - extract .bin from .exe file and copy into FAT32 partition.
[https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098](https://askubuntu.com/questions/539120/how-to-perform-a-hp-bios-upgrade-with-only-ubuntu/1234098#1234098) & 
[https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498](https://h30434.www3.hp.com/t5/Notebooks-Archive-Read-Only/How-to-update-BIOS-on-Linux/m-p/5441775#M1205498)

---

### Post by TheFu on 2021-09-22
Did you read what you posted?
```
Vulnerability Itlb multihit:     KVM: Mitigation: VMX unsupported 
Vulnerability L1tf:              Mitigation; PTE Inversion 
Vulnerability Mds:               Mitigation; Clear CPU buffers; SMT vulnerable 
Vulnerability Meltdown:          Mitigation; PTI 
Vulnerability Spec store bypass: Mitigation; Speculative Store Bypass disabled via prctl and seccomp 
Vulnerability Spectre v1:        Mitigation; usercopy/swapgs barriers and __user pointer sanitization 
Vulnerability Spectre v2:        Mitigation; Full generic retpoline, IBPB conditional, IBRS_FW, STIBP conditional, RSB filling 
Vulnerability Srbds:             Mitigation; Microcode 
Vulnerability Tsx async abort:   Not affected
```
For some Intel CPUs, these mitigations drastically impact performance.  Some just a few %, but others 20%+.  If you want more performance, research each of those and decide if disabling the mitigation is something you want.
> It found while the impacts vary tremendously from virtually nothing too significant on an application-by-application level, the collective whack is ~15-16 per cent on all Intel CPUs without Hyper-Threading disabled. Disabling increases the overall performance impact to 20 per cent (for the 7980XE), 24.8 per cent (8700K) and 20.5 per cent (6800K).
Ref: [https://www.fudzilla.com/news/pc-hardware/48726-benchmarks-show-how-much-spectre-and-meltdown-mitigation-slow-intel-chips](https://www.fudzilla.com/news/pc-hardware/48726-benchmarks-show-how-much-spectre-and-meltdown-mitigation-slow-intel-chips)

Sorry, finding non-Windows information on the performance hit wasn't easy and I'm not exactly loving the fudzilla.com link. Maybe your google-fu is stronger?

I'd try an older kernel.  The 5.11.x kernels seem to have more issues than normal.  Also, don't confuse "new" with "better". Running a non-LTS OS is a little scary to me.  Canonical often puts poorly tested software into their non-LTS releases.  The only time I've run a non-LTS release, outside testing, was when the LTS release refused to install on my new-ish hardware.  Even then, the non-LTS was run only for a few months until the LTS was released with support for the new CPU/GPU in that 1 system.

---

### Post by bradleypariah on 2021-09-22
> **TheFu said:**
> Did you read what you posted?
Being totally honest - despite being a Linux user for 12 years, and actually ditching Windows entirely in 2018, I'm still just an end-user.  I don't know what to do with that output.  I have absolutely no idea how to turn a mitigation off.  (EDIT) - I found this.  Does this look like the right way to do it?
[https://sleeplessbeastie.eu/2020/03/27/how-to-disable-mitigations-for-cpu-vulnerabilities/](https://sleeplessbeastie.eu/2020/03/27/how-to-disable-mitigations-for-cpu-vulnerabilities/) 

> **TheFu said:**
> I'd try an older kernel.... Running a non-LTS OS is a little scary to me. 
This laptop was running 18.04 before running 20.04.  I finally just got sick of the performance, and I've decided to dive into this issue, and decide once and for all if I need to replace this machine, hence trying out 21.04.
I've tried various flavors of Ubuntu, both LTS and non-LTS, Deepin, Manjaro, Solus, etc. and this machine takes forever to do anything no matter which distro I'm running.

I did find one other piece of information strange though.  The laptop has an Nvidia sticker on the deck, and Lenovo's website says that "some" of the 1570 models have a dedicated GPU.
However, when I open Driver Manager from System Settings, it says no proprietary drivers are available for my system, and my System Information page says I'm only running an integrated Intel GPU via Mesa drivers.  I wonder if the GPU is dead?  -but wouldn't that show some error somewhere?

> **oldfred said:**
> Do not know if something like this also works?
HP UEFI update - extract .bin from .exe file and copy into FAT32 partition.
I went ahead and created a post on the Lenovo forum, and told them I'm running Linux.  We'll see if I get any BIOS update guidance.  Kinda doubt it, but we'll see.  Worst case scenario, I'll go digging through the basement for a Win7 install DVD, and run Windows long enough to install the update, just to rule that out.

---

### Post by TheFu on 2021-09-22
> **bradleypariah said:**
>    Worst case scenario, I'll go digging through the basement for a Win7 install DVD, and run Windows long enough to install the update, just to rule that out.

You can download a Win10 "trial" version directly from MSFT.  I think it won't update/patch, but for your needs, that could be a better answer?  Also, not all BIOS update tools support Win7 at this point.

With your next machine purchase, might want to get one with a motherboard that supports BIOS updates directly - no OS needed.  Many Asus MBs do that.

---

### Post by rsteinmetz70112 on 2021-09-22
I don't know about yours but my Lenova laptop has an alphameric model number which indicates the complete original specification including all original options. Of course if you update anything that won't help but it should tell you if you have an Nvidia GPU in addition to the Intel.

---

### Post by bradleypariah on 2021-09-23
> **rsteinmetz70112 said:**
> I don't know about yours but my Lenova laptop has an alphameric model number which indicates the complete original specification including all original options. Of course if you update anything that won't help but it should tell you if you have an Nvidia GPU in addition to the Intel.

Mine is a Flex 3 1570 "80JM"
It has an Nvidia card.

Not sure when this got changed, but my discrete GPU was disabled in BIOS.  
I've got the 470 driver installed now, but the laptop is still slow.

---

### Post by bradleypariah on 2021-09-23
> **TheFu said:**
> 
For some Intel CPUs, these mitigations drastically impact performance.  Some just a few %, but others 20%+.  If you want more performance, research each of those and decide if disabling the mitigation is something you want.

I have now disabled all mitigations, but this laptop is still considerably slower than one with lower specs.
My HP with lower specs is still roughly twice as fast at everything, from booting up to opening a file browser.  I've poked around in BIOS, and nothing indicates this machine is being purposefully hindered.
I have opened the case, and the fan is completely clean.  No dust or hair.  The laptop never gets warmer than 45°C.
I just don't get it.

---

### Post by VMC on 2021-09-23
I'm guessing both use the same OS. You mentioned Kubuntu. Have you thought trying a lighter OS, say Lubuntu on both. Are they partitioned the same way, both use EFI, etc
Compare services used on both:
```
systemctl list-unit-files --state=enabled --no-pager
```

---

### Post by bradleypariah on 2021-09-23
> **VMC said:**
> I'm guessing both use the same OS. You mentioned Kubuntu. Have you thought trying a lighter OS, say Lubuntu on both.

They are both running Kubuntu 21.04 right now.  They are both fairly fresh installs, and they have the exact same set of apps.  
This is an issue I've been facing for months.  The Lenovo is perceptibly slow on other distros too.
I suppose Lubuntu might be faster than Kubuntu, but I don't merely want to speed up the Lenovo, I want to find out why the HP with an older SSD, two fewer GB of RAM, a slower CPU, and no GPU is still more than twice as fast.
There's clearly something wrong with the Lenovo.  I'm not expecting it to run The Witcher 3 on ultra or anything.  I just expect it to act like a 6-year-old laptop, but it's acting like it's 20.
It runs rock solid, but everything takes forever to load.  
I'm starting to wonder if it's because the Lenovo has single-channel memory, while the HP has two sticks?  What else could it be?

---

### Post by TheFu on 2021-09-23
I'm thinking it is hardware still.  Work through the log files and correct each warning and error 
or understand why they aren't important.
Hardware can still work, but be failing.  HDDs do this all the time - just much slower.  Poor network connections due to a crimped cable or wifi interference can have similar performance implications.

---

### Post by bradleypariah on 2021-09-25
Please check this out:[B]
VIDEO - Windows launching Firefox faster than Kubuntu [/B][URL="https://youtu.be/PAy0bOF5H1o"]https://youtu.be/PAy0bOF5H1o
[/URL]
Okay, I went ahead and installed Windows in order to install the BIOS/UEFI update, but Firefox still takes about 15 seconds to launch in Kubuntu.
I decided to do a little experiment.
While Windows was still on the SSD, I took a video of Firefox opening from Windows, and timed it vs. the speed on Kubuntu.
When I hit the quick key for Firefox in Windows, I kid you not, the Window is open in one single second.  Loading the Firefox New Tab page takes an additional eight seconds, but whatever.
The surprising thing is that Kubuntu takes ELEVEN seconds for the window to even appear, and additional four seconds to load the New Tab page.
Why on earth is this happening??

{EDIT}
One thing I noticed, which seems important:
Windows ***was***  slow too, but only at first.  I went to Lenovo's website, and  downloaded every driver they had.  Card reader, chipset, Bluetooth,  etc., until nothing in Device Manager had an exclamation point next to  it.  It was only then that the laptop felt like it "came loose."  Like  it became unchained or something.  I'm wondering if there is hardware in  this laptop that a default Linux install just doesn't know how to  efficiently handle.  How would I look into something like that?  Should I  bother?  Am I on to something, or should I just sell this thing with  Win 10/11 on it, and buy something made specifically for Linux?  I  really like this thing (when it works).

---

### Post by TheFu on 2021-09-25
Windows has something called the "pre-cache".  Look that up. 
There is also the pre-fetch loader. [https://en.wikipedia.org/wiki/Prefetcher](https://en.wikipedia.org/wiki/Prefetcher) It is a trick to make things seem faster than they really are. 

Virtual memory management on Unix is very different from Windows.  It can be massively tuned on Linux, if that is your need.  Most tuning will make it worse, however.  Experts only, but give it a shot.

Some laptops have special, Windows-only hardware. That is true. Intel added a disk cache on some of their systems a few years ago and only make Windows drivers. There isn't much we can do about that.

---

### Post by Yellow Pasque on 2021-09-25
Have you tried disabling "Baloo" (file indexing)? Sometimes, that thing goes crazy with disk usage due to bugs.
EDIT: I think it's under KDE's "Search" Settings

---

### Post by bradleypariah on 2021-09-25
> **Yellow Pasque said:**
> Have you tried disabling "Baloo" (file indexing)? Sometimes, that thing goes crazy with disk usage due to bugs.
EDIT: I think it's under KDE's "Search" Settings

Thanks for the suggestion.  I tried that, rebooted, and let everything settle.  The Firefox window still takes 8-9 seconds to appear, and the home page isn't loaded until 14-15 seconds.
No notable change.

> **TheFu said:**
> Some laptops have special, Windows-only hardware.  That is true. Intel added a disk cache on some of their systems a few  years ago and only make Windows drivers. There isn't much we can do  about that.

I'm becoming more and more convinced that's what happening with this laptop.  It's not Ubuntu's fault.  Even though I don't use Arch, I went ahead and installed Manjaro KDE, and it acts exactly the same.

Unfortunately, my ***actually*** faster laptop, the HP, has issues too.  It keeps randomly right-clicking when I'm typing, even though I have "disable touchpad while typing" enabled.  I'm not trying to ask for advice for that on this thread, I'm only pointing out that it looks like I'm in the market for a laptop now.

I guess I'll install Win10/11 on the Flex and sell it, then use the money to help pay for something designed for Linux.

Thanks for everyone's help.  Sad day.  :(

---

### Post by bradleypariah on 2021-09-25
Okay, hold the phone.  I created a post on the Lenovo forums, and someone told me to switch to Pop!_OS.
I though they were just blowing smoke, but DUDE, Pop launches the Firefox window in under one second, and has the New Tab page loaded in about two and a half seconds.
That's ***total time.***  2.5 seconds from desktop to homepage.
What kind of sorcery is this??  Does System 76 really add that much to the Ubuntu base??  -or is this rare for there to be such a difference?

Only "problem" is that I strongly dislike Gnome, and Cosmic is no better IMO.  I have nothing installed on this laptop, as it's been nuke'n'paved four or five times in the last couple days, so I'm halfway tempted to install Plasma on it and find out if that slows it down.  
I'll stick with Pop!_OS if it means I can keep my laptop.  It's quite positively faster than it was with Windows now.
It's exactly as fast as I would expect an i7 with 8GB of RAM and an Nvidia mobile GPU to be.
I press Super, the Dashboard opens/closes instantly.  Every app's window opens within one second of clicking its icon or shortcut.  I am floored.  

I guess I'll mark this thread as solved??  I'm still on an Ubuntu base, so I guess I'm cool with switching distros.  I honestly don't feel good that the solution to my problem was switching distros though.
Anybody have any closing thoughts?  I appreciate everyone's willingness to help.

---

### Post by TheFu on 2021-09-25
I don't restart by systems or a browser all that often, so I honestly don't know how quickly that specific test is.
Comparing a bloated KDE to a lite-gnome2-ish isn't really fair, but for most users, switching distros is a good way to see what's possible. Most Ubuntu systems are bloated.  

My main desktops begin with Ubuntu Server that has no GUI, only gets ssh install, then I build up the specific applications and services that I want.

From time to time, I'll load a stock version of Lubuntu, Xubuntu, Mate or the stock Ubuntu (gnome3) just to see what each team has done. Canonical definitely has an agenda to ensure every system has snap packages on it.  The slightly different drivers could easily be why PopOS is working better for you.  It would have been interesting to see the differences (for someone, not me), then perhaps we'd uncover what made it faster.  

Many things go into choosing a distro. We are each different.

For fun, a few days ago I loaded Xubuntu 20.04 for a different need (actually trying to setup automatic desktop pushes for 50 clients). I didn't  do anything related to performance testing. I think that system is still around somewhere.  2 CPU, 2G of RAM.  SSD.  I don't know if it has firefox.

11 seconds from boot to a login window.
4 seconds from password entry to full desktop.
4 seconds to start firefox until the full screen "Start here" was show.

Not really a high-power system:
```
$ **inxi** -b
System:
  Host: xubu-2004 Kernel: 5.4.0-86-generic x86_64 bits: 64 Console: tty 1 
  Distro: Ubuntu 20.04.3 LTS (Focal Fossa) 
Machine:
  Type: Kvm System: QEMU product: Standard PC (i440FX + PIIX, 1996) v: pc-i440fx-bionic 
  serial: <superuser/root required> 
  Mobo: N/A model: N/A serial: N/A BIOS: SeaBIOS v: 1.10.2-1ubuntu1 date: 04/01/2014 
CPU:
  **2x Single Core**: AMD Ryzen 5 2600 type: SMP speed: 3394 MHz 
Graphics:
  Device-1: driver: bochs-drm v: N/A 
  Display: server: X.org 1.20.11 driver: modesetting unloaded: fbdev,vesa tty: 91x45 
  Message: Advanced graphics data unavailable in console. Try -G --display 
Network:
  Device-1: Intel 82371AB/EB/MB PIIX4 ACPI type: network bridge driver: piix4_smbus 
  Device-2: Red Hat Virtio network driver: virtio-pci 
Drives:
  Local Storage: total: 10.00 GiB used: 4.43 GiB (44.3%) 
Info:
  Processes: 203 Uptime: 14m Memory: 1.94 GiB used: 591.0 MiB (29.7%) Init: systemd 
  runlevel: 5 Shell: bash inxi: 3.0.38 

$ free -h
              total        used        free      shared  buff/cache   available
Mem:          1.9Gi       500Mi       759Mi       9.0Mi       726Mi       1.3Gi
Swap:         1.0Gi          0B       1.0Gi
```

Using some tools that are built into all Ubuntus (systemd really) ...
```
$ **systemd-analyze**  | tee perf.log

Startup finished in 2.758s (kernel) + 7.194s (userspace) = 9.952s 
graphical.target reached after 6.347s in userspace

$ **systemd-analyze blame**  | tee -a  perf.log
1.407s systemd-udev-settle.service               
1.118s dev-mapper-ubuntu\x2d\x2dvg\x2droot.device
1.081s systemd-networkd-wait-online.service      
 915ms udisks2.service                           
 821ms cloud-init-local.service                  
 682ms cloud-config.service                      
 622ms accounts-daemon.service                   
 477ms cloud-init.service                        
 472ms networkd-dispatcher.service               
 464ms NetworkManager-wait-online.service        
 450ms ModemManager.service                      
 450ms cloud-final.service                       
 307ms NetworkManager.service                    
 280ms systemd-timesyncd.service                 
 279ms systemd-modules-load.service              
 257ms polkit.service                            
 240ms systemd-logind.service                    
 234ms [email]lvm2-pvscan@252:3.servic[/email]e                 
 216ms avahi-daemon.service                      
 215ms keyboard-setup.service                    
 209ms apparmor.service                          
 186ms systemd-resolved.service                  
 181ms switcheroo-control.service                
 171ms lvm2-monitor.service                      
 143ms systemd-sysctl.service                    
 142ms rsyslog.service                           
 139ms multipathd.service                        
 129ms systemd-journal-flush.service             
 126ms systemd-udevd.service                     
 112ms apport.service                            
 110ms wpa_supplicant.service                    
 106ms grub-common.service                       
  99ms e2scrub_reap.service                      
  90ms dev-ubuntu\x2dvg-swap.swap                
  82ms [email]user@1000.servic[/email]e                         
  77ms systemd-udev-trigger.service              
  75ms systemd-networkd.service
....
$ systemd-analyze critical-chain
The time when unit became active or started is printed after the "@" character.
The time the unit took to start is printed after the "+" character.

graphical.target @6.347s
&#9492;&#9472;udisks2.service @5.370s +915ms
  &#9492;&#9472;basic.target @5.270s
    &#9492;&#9472;sockets.target @5.269s
      &#9492;&#9472;uuidd.socket @5.268s
        &#9492;&#9472;sysinit.target @5.252s
          &#9492;&#9472;cloud-init.service @4.728s +477ms
            &#9492;&#9472;systemd-networkd-wait-online.service @3.643s +1.081s
              &#9492;&#9472;systemd-networkd.service @3.567s +75ms
                &#9492;&#9472;network-pre.target @3.565s
                  &#9492;&#9472;cloud-init-local.service @2.743s +821ms
                    &#9492;&#9472;systemd-remount-fs.service @855ms +19ms
                      &#9492;&#9472;systemd-journald.socket @789ms
                        &#9492;&#9472;-.mount @767ms
                          &#9492;&#9472;system.slice @767ms
                            &#9492;&#9472;-.slice @767ms

```
There's other stuff, but those are main things people can do something about without too much effort.  I typically purge network-manager and avahi and all snap stuff, since I don't need/want them and they slow boots greatly.

You can see that with just 10G of storage, there won't be any data local to these systems. 

**lshw** is useful to look for differences in hardware and settings and drivers.  Just boot the fast system and save the output to a file, then boot the slow system and save the output to a different file, then use either system to compare the files - diff, sdiff, meld are all nice tools.  People seem to really like **meld**. It is good to compare text files.

---

### Post by rsteinmetz70112 on 2021-09-27
If Pop! helped that much on your slower computer, I wonder what it would do on the other faster one?

---

### Post by bradleypariah on 2021-09-29
Well guys, I hate to do this, but I retract saying Pop!_OS was the solution.  It definitely isn't. 

I did find the reason this laptop is throttling though.

[SIZE=4]**[COLOR=#008000]It's because it's _*charging*_.  [/COLOR]**[/SIZE]:KS

[SIZE=4][SIZE=2]Have any of you ever heard of such a thing before? 
[/SIZE][/SIZE]I don't[SIZE=4][SIZE=2] have different Charging/Battery settings in Power Management. 
 I did not come by this latest revelation lightly.  I have benchmarks. I ran repeated back-to-back tests. Check this out:
[/SIZE][/SIZE][COLOR=#333333]
Launching Firefox, from the desktop to fully loading the New Tab page:[/COLOR]

[LIST]
[*]It takes 11 seconds when the laptop is charging.
[*]It takes 2 seconds while on battery.
[/LIST]

[COLOR=#333333]I installed sysbench, and ran [sysbench --test=cpu run].[/COLOR]

[LIST]
[*]While charging, the score is 1678 events with an average of 5.96ms latency.
[*]When on battery, the score is 9,992 events with an average of 1ms latency.
[/LIST]

[COLOR=#333333]Booting up:[/COLOR]

[LIST]
[*]It takes 42 seconds to get to the login screen while charging.
[*]It takes 16 seconds to get to the login screen on battery power.
[/LIST]

[COLOR=#333333]Loading the Plasma desktop[/COLOR]

[LIST]
[*]After pressing Enter, it takes 42 seconds for Plasma to fully load while charging.
[*]After pressing Enter, it takes 6 seconds for Plasma to fully load while on battery.
[/LIST]

This is seeming quite conclusive.  The reason my laptop was always slow is because it was always charging.  When I got sick of it, and started troubleshooting, installing Windows for the BIOS/UEFI update, and trying Solus, Clear Linux, Pop!_OS, etc., I was walking around the house.  It just so happens I was on battery power when I tried out Pop!_OS.  

Mystery solved.... ***BUT*** Do any of you know why this might be happening?  I searched all over in System Settings > Power Management, and I see nothing.  It should not be forgotten, this happens on Windows, on Pop!_OS, you name it.  This is the hardware's fault, not the OS/DE, but is there a way to tell the laptop not to throttle itself while charging? :confused:
(I am also going to ask the Lenovo Forums, in case they know)

---

### Post by bradleypariah on 2021-09-29
Welp, no sooner did I come to the conclusion that charging was the issue than I found this reply to a similar question on Quora:
[IMG]https://www.kubuntuforums.net/attachment.php?attachmentid=9548&d=1632930415[/IMG]https://www.quora.com/When-I-plug-the-power-cable-into-my-Lenovo-laptop-it-slows-down-the-CPU-speed-drops-Ive-taken-my-laptop-to-tech-support-several-times-but-nothing-Can-you-help-me-find-the-problem

> **"Mr One in a Million"]
[SIZE=2][COLOR=#282829][FONT=-apple-system]As per both the current answers.
Check settings and also check the psu.
My Lenovo has TWO psu options said:**
> [/COLOR]
[/SIZE][COLOR=#282829][FONT=-apple-system][SIZE=2]In my case they are a 65W psu and a 95W psu[/SIZE].[/FONT][/COLOR]

I just ordered a 90-watt PSU off eBay for twelve bucks.  Here's hoping that'll be the end of it.

---

