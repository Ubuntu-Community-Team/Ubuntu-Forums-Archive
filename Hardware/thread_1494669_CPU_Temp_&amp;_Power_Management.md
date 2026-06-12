---
title: "CPU Temp &amp; Power Management"
date: 2010-05-27
forum: Hardware
---

### Post by Tomarse on 2010-05-27
Hi, I'm a recent convert to Linux. I did have dual boot XP and Ubuntu on my HP510 Laptop, but have recently cleared the hard drive and now am only running Ubuntu 10.04 LTS. Since then my CPU has been running at really high temps, and I've even had the laptop cut out a couple of times due to critical temp being reached.

Below is a recent temp reading, and all I have open is FireFox and the Terminal.
[COLOR=Navy]state:                   ok
temperature:             77 C
critical (S5):           100 C
thomas@Hades:~$ sudo cat /proc/acpi/fan/*/*
cat: /proc/acpi/fan/*/*: No such file or directory[/COLOR]

I checked my CPU info, and noticed that there are no details for "power management".
[COLOR=Navy]processor    : 0
vendor_id    : GenuineIntel
cpu family    : 6
model        : 13
model name    : Intel(R) Pentium(R) M processor 2.26GHz
stepping    : 8
cpu MHz        : 2267.000
cache size    : 2048 KB
fdiv_bug    : no
hlt_bug        : no
f00f_bug    : no
coma_bug    : no
fpu        : yes
fpu_exception    : yes
cpuid level    : 2
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts est tm2
bogomips    : 2385.08
clflush size    : 64
cache_alignment    : 64
address sizes    : 32 bits physical, 32 bits virtual
power management:[/COLOR]

Did I wipe the CPUs power management driver when I removed XP? If so, is there any way to get it back?

Any help would be appreciated.

Cheers

Tom

---

