---
title: "Problem seeing all 4 cores of Quad-core AMD system"
date: 2009-02-07
forum: Hardware
---

### Post by ectospasm on 2009-02-07
I have a quad-core processor, and an SMP kernel installed, and yet only one core is getting recognized by the kernel:

```
amphetamine:~ # cat /proc/cpuinfo
processor    : 0
vendor_id    : AuthenticAMD
cpu family    : 16
model        : 2
model name    : AMD Phenom(tm) 9950 Quad-Core Processor
stepping    : 3
cpu MHz        : 1300.000
cache size    : 512 KB
physical id    : 0
siblings    : 1
core id        : 0
cpu cores    : 1
apicid        : 0
initial apicid    : 0
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 5
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips    : 5199.86
clflush size    : 64
power management: ts ttp tm stc 100mhzsteps hwpstate

amphetamine:~ # uname -a
Linux amphetamine 2.6.27-11-generic #1 SMP Thu Jan 29 19:24:39 UTC 2009 i686 GNU/Linux
amphetamine:~ # 

```I know it works, because it has definitely loaded all four cores before.  I first noticed the problem a couple of days ago, when I couldn't load my VMWare Server image.  The VM image requires two cores, and it complains that I've only got one core installed.  I was able to get all four cores back by rebooting then, but that's not the case now.

I did turn off the quiet boot, and it seemed like the kernel recognized all four cores (I guess, it blanked the screen before I could read the output from the fourth core).  But still /proc/cpuinfo reports the one core.

Help?  This is really annoying.

EDIT:  It looks like what I saw above is the CPU timers.  It does NOT seem to register at all that there are four cores there.  I've tried the kernel you see above, and also the 2.6.27-9 kernel (which I know worked in the past).  Windows XP on the exact same system seems to recognize all four cores (afaict, I'm not a Windows guy).  I KNOW this worked before, because my VM mentioned above won't run the way it's configured if there are any less than two cores on my host system.  I'm including cat /proc/cmdline, for good measure:

```
amphetamine:~ # cat /proc/cmdline 
root=UUID=5b026cc0-09be-4255-8023-54c95619ca42 ro splash
```

---

