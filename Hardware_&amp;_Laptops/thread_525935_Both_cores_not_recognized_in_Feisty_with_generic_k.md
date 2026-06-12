---
title: "Both cores not recognized in Feisty with generic kernel"
date: 2007-08-14
forum: Hardware &amp; Laptops
---

### Post by xghstst0riesx on 2007-08-14
I have a Dell E1505 with the original Core Duo processor. I am dual booting plain Ubuntu and Windows XP. 
Only one processor is being recognized. I have checked my /boot/grub/menu.lst and I am using the generic kernel. The only other thing I can think of is that the proprietary driver (fglrx) i am using for my ATI Mobility Radeon X1300 could somehow be interfering, but I really don't know. Any ideas?

---

### Post by kostkon on 2007-08-15
How did you find out that only one core is used? If you open *System Monitor* does indeed shows you only one processor?

The generic kernel should use both cores without any problems, out of the box.

---

### Post by xghstst0riesx on 2007-08-15
Yep, System Monitor only shows one. Also, here's is the output of "cat /proc/cpuinfo" :
```

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 14
model name      : Genuine Intel(R) CPU           T2400  @ 1.83GHz
stepping        : 8
cpu MHz         : 1000.000
cache size      : 2048 KB
physical id     : 0
siblings        : 1
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 10
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx constant_tsc up pni monitor vmx est tm2 xtpr
bogomips        : 3665.96
clflush size    : 64


```

---

### Post by xghstst0riesx on 2007-08-25
bump :)

---

### Post by diffuze on 2007-08-25
I might be totallly wrong here but are you using 32 bit ubuntu?
I'm usring 64 bit and both my cores are recognized.
```
processor       : 0
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 2
cpu MHz         : 2211.388
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 4426.32
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

processor       : 1
vendor_id       : AuthenticAMD
cpu family      : 15
model           : 75
model name      : AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
stepping        : 2
cpu MHz         : 2211.388
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 1
cpu cores       : 2
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow pni cx16 lahf_lm cmp_legacy svm cr8_legacy
bogomips        : 4422.95
TLB size        : 1024 4K pages
clflush size    : 64
cache_alignment : 64
address sizes   : 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc

```
I can't compare  because I don't have the 32 bit version installed.

---

### Post by dabl on 2007-08-25
Using the -generic kernel, both CPU cores should be recognized, regardless of whether it is i386 or 64-bit. I have a Core 2 Extreme, and both cores are recognized in both Kubuntu 32-bit and Ubuntu 64-bit.

I wonder if "power management" has anything to do with this problem?  If it's a laptop, and trying to save power, it may be that some of the apci, lapic, etc.( things that I don't use on my desktop system) has decided only 1 CPU core is needed at the moment.

If you exercise it by ripping a CD or something, it might wake up the other core for that kind of CPU-intensive work.  :)

---

### Post by xghstst0riesx on 2007-09-08
bump again

---

### Post by RU-In? on 2007-09-08
I found this thread a couple of weeks ago because I was experiencing the same symptoms. I had just re-installed feisty and I noticed a few days later that only one processor was being reported in system monitor. I am using feisty with a 2.8 GHz Pentium 4 with HyperThreading. This bugged me until it dawned on me, after reading an SMP article in my searches, that I normally perform the installation process (on this box) with the "acpi lapci=off" boot option, and that I had neglegted to turn it back on in the /boot/grub/menu.lst file after the install. So I did (and a reboot), and this fixed the problem for me. I noticed that some related postings pointed to the /boot/grub/menu.lst file, but not  towards the specific detail that you have to have acpi enabled for SMP to function. I changed mine to read "acpi=on" and this works, I thought of just omitting "acpi=off" but thought that the "=on" switch would ensure success and had left it that way. I hope that this helps some of you, if not all of you :), it sure made me feel better... I had it before, I want it now!

Just to clearify: when SMP was not functioning on my system, there was also a "acpi=off" at the end of the kernel entry in the menu.lst file. I changed it to read "acpi=on" instead.
:
here is the entry for the first kernel option in my now SMP freindly menu.lst file:

kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=*[UUID of your hard drive*]  ro quiet splash live** acpi=on**


Happy Hackin!

---

### Post by xghstst0riesx on 2007-09-11
Alright, I finally figured it out. I had the options "noapic nolapic" at the end of my kernel option in /boot/grub/menu.lst so I removed them and now the second CPU is recognized. I think I needed them when installing since my video card wasn't working. 
Thanks everyone for the help.

:guitar: Dual cores!

---

