---
title: "C2D: Only one CPU detected after resuming from suspend"
date: 2008-05-12
forum: Hardware
---

### Post by fulat2k on 2008-05-12
Hi folks,

I'm using a Dell Latitude D630 with C2D T7100.  Weird thing happens when I resume from suspend.  One of the cores isn't detected properly after the system is resumed.  Here's what I get from cpufreq-info:

```
cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to linux@brodo.de, please.
analyzing CPU 0:
  driver: acpi-cpufreq
  CPUs which need to switch frequency at the same time: 0
  hardware limits: 800 MHz - 1.80 GHz
  available frequency steps: 1.80 GHz, 1.80 GHz, 1.20 GHz, 800 MHz
  available cpufreq governors: powersave, conservative, ondemand, userspace, performance
  current policy: frequency should be within 800 MHz and 1.80 GHz.
                  The governor "userspace" may decide which speed to use
                  within this range.
  current CPU frequency is 1.80 GHz.
analyzing CPU 1:
  no or unknown cpufreq driver is active on this CPU

```

Any idea what's wrong?


Thanks.

---

### Post by sdennie on 2008-05-12
Do you only see 1 CPU if you do a:

```

cat /proc/cpuinfo

```

If so, I can't think of anything other than seeing if there is a BIOS update for your machine.  There may be other options but, that's one worth looking into.

---

### Post by fulat2k on 2008-05-12
I see two CPUs.  

```
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
stepping        : 13
cpu MHz         : 1800.000
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida
bogomips        : 3596.70
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
stepping        : 13
cpu MHz         : 1794.048
cache size      : 2048 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida
bogomips        : 3590.13
clflush size    : 64
```

---

### Post by blankphoto on 2008-05-12
im getting this for that command

cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 15
model name	: Intel(R) Core(TM)2 CPU          6400  @ 2.13GHz
stepping	: 6
cpu MHz		: 2128.418
cache size	: 2048 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm
bogomips	: 4287.37
clflush size	: 64


Any idea how to force detection? This was working fine for like 3 weeks and now this.

cpufreq-info gives this after reboot

cpufrequtils 002: cpufreq-info (C) Dominik Brodowski 2004-2006
Report errors and bugs to [email]linux@brodo.de[/email], please.
analyzing CPU 0:
  no or unknown cpufreq driver is active on this CPU


Update: I have verified throught the Live CD that both cores are functioning, but the installed version is not finding one of them.

---

### Post by blankphoto on 2008-05-12
any help would be greatly appreciated.

thank you.

---

### Post by sdennie on 2008-05-12
fulat2k, can you post the output of the following two commands:

```

ls -l /sys/devices/system/cpu
ls -l /sys/devices/system/cpu/cpu?

```

Some (most?) machines end up creating symlinks to the cpu frequency governor so that changing one changes the other.  It's possible that the link isn't being restored after suspend somehow.

---

### Post by sdennie on 2008-05-12
blankphoto, I'm not sure what that problem might be.  Are you using the default Hardy kernel?

---

### Post by blankphoto on 2008-05-12
I am that I know of, unless mediabuntu (the one for dvd and movies) has a different kernel.

Also my audio is affected in the installed system.

is there a way to tell linux to look at the hardware again, like a fresh istall but without loosing all the packages i've installed?

---

### Post by fulat2k on 2008-05-12
vor, here's what I get after a system restart:

```
# ls -l /sys/devices/system/cpu/
total 0
drwxr-xr-x 6 root root    0 2008-05-13 11:37 cpu0
drwxr-xr-x 5 root root    0 2008-05-13 11:37 cpu1
drwxr-xr-x 2 root root    0 2008-05-13 11:39 cpuidle
-rw-r--r-- 1 root root 4096 2008-05-13 11:39 sched_mc_power_savings

ls -l /sys/devices/system/cpu/cpu?
/sys/devices/system/cpu/cpu0:
total 0
drwxr-xr-x 5 root root    0 2008-05-13 11:39 cache
drwxr-xr-x 4 root root    0 2008-05-13 11:37 cpufreq
drwxr-xr-x 5 root root    0 2008-05-13 11:39 cpuidle
-r-------- 1 root root 4096 2008-05-13 11:39 crash_notes
drwxr-xr-x 2 root root    0 2008-05-13 11:39 topology

/sys/devices/system/cpu/cpu1:
total 0
drwxr-xr-x 5 root root    0 2008-05-13 11:39 cache
lrwxrwxrwx 1 root root    0 2008-05-13 11:37 cpufreq -> ../../../../devices/system/cpu/cpu0/cpufreq
drwxr-xr-x 5 root root    0 2008-05-13 11:39 cpuidle
-r-------- 1 root root 4096 2008-05-13 11:39 crash_notes
-rw-r--r-- 1 root root 4096 2008-05-13 11:39 online
drwxr-xr-x 2 root root    0 2008-05-13 11:39 topology

```

Here's what I get after I resume from suspend:

```
# ls -l /sys/devices/system/cpu/cpu?
/sys/devices/system/cpu/cpu0:
total 0
drwxr-xr-x 5 root root    0 2008-05-13 11:39 cache
drwxr-xr-x 4 root root    0 2008-05-13 11:46 cpufreq
drwxr-xr-x 5 root root    0 2008-05-13 11:39 cpuidle
-r-------- 1 root root 4096 2008-05-13 11:39 crash_notes
drwxr-xr-x 2 root root    0 2008-05-13 11:39 topology

/sys/devices/system/cpu/cpu1:
total 0
drwxr-xr-x 5 root root    0 2008-05-13 11:46 cache
drwxr-xr-x 5 root root    0 2008-05-13 11:39 cpuidle
-r-------- 1 root root 4096 2008-05-13 11:39 crash_notes
-rw-r--r-- 1 root root 4096 2008-05-13 11:39 online
drwxr-xr-x 2 root root    0 2008-05-13 11:47 topology
```

You're spot on.  The sym link was not re-established.  Let me try relinking and see if cpufreq picks up the change.

UPDATE: Scratch that.  I can't rm -rf cpu1/cpuidle.  Is this a known issue?

Thanks.

---

### Post by blankphoto on 2008-05-13
My problem got [solved]("http://ubuntuforums.org/showthread.php?p=4946702#post4946702").

Thank you for trying Vor.

---

### Post by fulat2k on 2008-05-13
Hi folks,

Any fix for this problem?

THanks.

---

### Post by fulat2k on 2008-06-22
Oohh.. I think they've fixed it in the latest kernel update.  2.6.24-19 :D

---

