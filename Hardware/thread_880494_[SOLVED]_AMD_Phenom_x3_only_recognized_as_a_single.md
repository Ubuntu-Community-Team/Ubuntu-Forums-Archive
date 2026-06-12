---
title: "[SOLVED] AMD Phenom x3 only recognized as a single core"
date: 2008-08-05
forum: Hardware
---

### Post by AFarris01 on 2008-08-05
Hey all...ive got an issue with a computer i build for somebody, that is fairly serious, and i cant seem to find any relevent info on how to fix it:

It has been built with an AMD Phenom x3 8400, BIOS is fully up-to-date and fully supports the x3 series, however ubuntu only recognizes one of the cpu's cores.  Ive seen all over the forums of people using older/different kernels, and the suggested fix has always been 'use the -generic kernel.' however, in this case, the generic kernel is already in use, and its not working... Heres the CLI outputs relevant to this problem:

user@Trill:~$ uname -a
Linux Trill 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux

--------------------------------------------
user@Trill:~$ cat /proc/cpuinfo 
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
**model name	: AMD Phenom(tm) 8400 Triple-Core Processor**
stepping	: 2
cpu MHz		: 2100.280
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
**cpu cores	: 1**
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc pni cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs ts ttp tm stc 100mhzsteps hwpstate
bogomips	: 3203.07
clflush size	: 64

-------------------------------------------
user@Trill:~$ dpkg -l | grep kernel

ii  libdrm2                                    2.3.0-4ubuntu1                Userspace interface to kernel DRM services -
ii  linux-generic                              2.6.24.16.18                  Complete Generic Linux kernel
ii  linux-headers-2.6.24-16                    2.6.24-16.30                  Header files related to Linux kernel version
ii  linux-headers-2.6.24-16-generic            2.6.24-16.30                  Linux kernel headers for version 2.6.24 on x
ii  linux-headers-generic                      2.6.24.16.18                  Generic Linux kernel headers
ii  linux-image-2.6.24-16-generic              2.6.24-16.30                  Linux kernel image for version 2.6.24 on x86
ii  linux-image-generic                        2.6.24.16.18                  Generic Linux kernel image
ii  linux-restricted-modules-generic           2.6.24.16.18                  Restricted Linux modules for generic kernels
ii  module-init-tools                          3.3-pre11-4ubuntu5            tools for managing Linux kernel modules
ii  nvidia-kernel-common                       20051028+1ubuntu8             NVIDIA binary kernel module common files
ii  udev                                       117-8                         rule-based device node and kernel event mana
--------------------------------------------------

Basically i just want to know...does anybody know what this issue might be, or how i can fix it?  i appreciate any thoughts!

Andrew

---

### Post by AFarris01 on 2008-10-09
Just wanted to post and say that the issue has been repaired by an installation of a 64 bit version of ubuntu as most of the sources i've found suggested.  previously that wasn't an option, but something recently went wrong with ndiswrapper and the kernel would just drop into an infinite loop on boot.  i took that opportunity to suggest a 64 bit OS, which subsequently fixed all issues.

SOLVED!

---

### Post by sunny_pirate on 2010-01-16
Hello,

I have a similar problem.

cat /proc/cpuinfo shows:

processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 2
**model name	: AMD Phenom(tm) 8450 Triple-Core Processor**
stepping	: 3
cpu MHz		: 2109.506
cache size	: 512 KB
physical id	: 0
siblings	: 1
core id		: 0
**cpu cores	: 1**
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc up rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs
bogomips	: 4219.00
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate


I have tried everything from installing the 64 bit version (Karmic) to changing the USB setting to Fullspeed. Also my BIOS detects all 3 cores but Ubuntu fails to detect the same.
Please Help.

---

### Post by autumnraine on 2010-07-03
I'm having a similar problem, for some reason recently my Shuttle SN78SH7 with a Phenom X3 only recognizes one core 4 of 5 boots, if it boots at all. I know that with my particular model there's trouble with USB recognition or something, though XP recognizes everything flawlessly sadly... The problem's not just with Ubuntu though, I've had similar issues with Mandriva and Fedora. I'll try removing my usb devices to see if that resolves it. 

Is anyone else still having these issues?

---

