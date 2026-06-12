---
title: "powernowd with Intel Atom 330 CPU1 not scaling frequency"
date: 2012-08-14
forum: Hardware
---

### Post by ckohrt on 2012-08-14
Hello!

I have a problem with my Nettop with an Intel Atom 330 processor using powernowd to scale the frequency. I am using "Ubuntu 10.04.4 LTS \n \l" reported by  ```
cat /etc/issue
```.

I have installed everything and the scaling works for cpu0 and cpu2. If I look to the config files under /sys/devices/system/cpu/cpu2/cpufreq, it is reported a symlink, which is just fine.

The problem is cpu1 (and cpu3, which has also a symlink to cpu1). The frequency stays at 1,5GHz regardless what I tell powernowd, e.g.:

```

root@revo:~# powernowd  -m 2 -l 50 -u 90 -s 50000 -c 2
powernowd: PowerNow Daemon v1.00, (c) 2003-2008 John Clemens
powernowd: Found 2 scalable units:  -- 2 'CPUs' per scalable unit
powernowd:   cpu0: 199Mhz - 1599Mhz (29 steps)
powernowd:   cpu1: 199Mhz - 1599Mhz (29 steps)
powernowd:   cpu2: 199Mhz - 1599Mhz (29 steps)
powernowd:   cpu3: 199Mhz - 1599Mhz (29 steps)

```

This seems to be correct, but cpu1/3 are not working.

Even when I look to the available governors, it looks good:
```

cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_available_governor
conservative ondemand userspace powersave performance

```When I try to set another governor manually with:
```

echo powersave > /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
echo powersave > /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor

```The frequency shows:
```

sudo watch -n 1 cat /sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq
199999

```...and...
```

sudo watch -n 1 cat /sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_cur_freq
199999

```...so it's generally working.
The powersave governor stays at 199999, so for me it's useless. I cannot set the ondemand and the conservative governor, but for powernod, the only relevant governor is userspace, which is automatically set correctly on powernowd start:

```

cat /sys/devices/system/cpu/cpu0/cpufreq/scaling_governor
userspace

``````

cat /sys/devices/system/cpu/cpu1/cpufreq/scaling_governor
userspace

```So, what can I checkto get powernowd working for cpu1/3?

To solve this, I have tried to create a symlink from /sys/devices/system/cpu/cpu1/cpufreq --> /sys/devices/system/cpu/cpu0/cpufreq but I was not successfull, because this was not allowed. I read somewhere, that this is also handled in GRUB2 but reconfiguring GRUB2 did not fix the issue.

Maybe there are some kernel stuff her like:
```

sudo modprobe p4-clockmod

```...was successfull.

It has been reported somewher, that the p4-clockmod has some issues with multi core processors. But the newest version should have been fixed theses issues. 

CPU Info:
```

cat /proc/cpuinfo                                                                        processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 28
model name      : Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping        : 2
cpu MHz         : 199.999
cache size      : 512 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 2
apicid          : 0
initial apicid  : 0
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips        : 3199.69
clflush size    : 64
cache_alignment : 64
address sizes   : 32 bits physical, 48 bits virtual
power management:

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 28
model name      : Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping        : 2
cpu MHz         : 1599.996
cache size      : 512 KB
physical id     : 0
siblings        : 4
core id         : 1
cpu cores       : 2
apicid          : 2
initial apicid  : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips        : 3200.05
clflush size    : 64
cache_alignment : 64
address sizes   : 32 bits physical, 48 bits virtual
power management:

processor       : 2
vendor_id       : GenuineIntel
cpu family      : 6
model           : 28
model name      : Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping        : 2
cpu MHz         : 199.999
cache size      : 512 KB
physical id     : 0
siblings        : 4
core id         : 0
cpu cores       : 2
apicid          : 1
initial apicid  : 1
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips        : 3200.00
clflush size    : 64
cache_alignment : 64
address sizes   : 32 bits physical, 48 bits virtual
power management:

processor       : 3
vendor_id       : GenuineIntel
cpu family      : 6
model           : 28
model name      : Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping        : 2
cpu MHz         : 1599.996
cache size      : 512 KB
physical id     : 0
siblings        : 4
core id         : 1
cpu cores       : 2
apicid          : 3
initial apicid  : 3
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips        : 3200.02
clflush size    : 64
cache_alignment : 64
address sizes   : 32 bits physical, 48 bits virtual
power management:

```Mod info:
```

lsmod
Module                  Size  Used by
ppdev                   6375  0
autofs4                28231  1
arc4                    1473  2
fbcon                  39270  71
tileblit                2487  1 fbcon
font                    8053  1 fbcon
p4_clockmod             4588  2
bitblit                 5811  1 fbcon
speedstep_lib           4055  1 p4_clockmod
softcursor              1565  1 bitblit
vga16fb                12757  1
vgastate                9857  1 vga16fb
ath5k                 134405  0
mac80211              238864  1 ath5k
ath                     9723  1 ath5k
psmouse                65040  0
lp                      9336  0
cfg80211              148725  3 ath5k,mac80211,ath
parport                37160  2 ppdev,lp
serio_raw               4950  0
i2c_nforce2             6099  0
led_class               3764  1 ath5k
shpchp                 33679  0
nvidia              10833082  0
raid10                 21450  0
raid456                54720  0
async_pq                3891  1 raid456
async_xor               3111  2 raid456,async_pq
xor                     4685  1 async_xor
async_memcpy            1537  1 raid456
async_raid6_recov       1816  1 raid456
usb_storage            50601  1
raid6_pq               80147  2 async_pq,async_raid6_recov
async_tx                2545  5 raid456,async_pq,async_xor,async_memcpy,async_raid6_recov
ahci                   38350  2
forcedeth              55624  0
raid1                  22514  0
raid0                   6778  0
multipath               7181  0
linear                  4126  0

```Any help appreciated!

Thanks in advance!
Christian

---

### Post by ckohrt on 2012-09-05
Found the answer by accident:

powernowd  -m 2 -l 50 -u 90 -s 50000 -c 1

is working.

---

### Post by ahallubuntu on 2012-09-05
Out of curiosity, what exactly are you trying to accomplish?  The N330 very little power.  My Atom N330 system idles at 28 watts but even under load it only hits 32 watts.  Scaling the frequency down isn't going to save much power if any.  My N330 board doesn't even have a fan on the Atom CPU, only on the chipset.

---

