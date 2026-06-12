---
title: "Multi-Core+Multi-CPU"
date: 2010-08-13
forum: Hardware
---

### Post by J_Boner on 2010-08-13
Ok guys and gals,
I am running a Zotac ION-ITX, believe model D, It has 2x Intel Atom N330 processors. Each of these has 2 cores. So basically I have a quad-core system. Runs absolutely spectacular with Ubuntu 10.04.1 LTS. I am loving the setup.

What I am wondering is how the following cpuinfo file from /proc reads them as such but in system monitor and my "infopanel" for screenlets only reads 2. I would love to see the breakdown for each core instead of each cpu. How would one achieve this? I know this can be done because it was done in Fedora 12/13 gnome. (Fedora 12/13 were both too buggy and did wierd actions w/ networking on this machine so tried Ubuntu 10.04 and got what I wanted.)

So, anyway, how do i get this damn thing to read usage by core instead of by cpu?

/proc/cpuinfo:

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping	: 2
cpu MHz		: 1599.961
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips	: 3199.92
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping	: 2
cpu MHz		: 1599.961
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 2
initial apicid	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips	: 3199.99
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 48 bits virtual
power management:

[IMG]http://farm5.static.flickr.com/4120/4888447707_2001392f48_z.jpg[/IMG]

Thanks for any help, and hope to resolve this!

J_Boner

---

### Post by J_Boner on 2010-08-13
*bump*

---

### Post by Zeike on 2010-08-13
Are you sure this has 2x Atoms?  That sounds very strange.

And there is no mention of two processors here: [http://www.zotacusa.com/zotac-ionitx-a-u-atom-n330-1-6ghz-dual-core-mini-itx-intel-motherboard.html](http://www.zotacusa.com/zotac-ionitx-a-u-atom-n330-1-6ghz-dual-core-mini-itx-intel-motherboard.html)

Each of those 'processors' in the /proc/cpuinfo are, in fact, individual cores.

---

### Post by sdennie on 2010-08-13
The output of /proc/cpuinfo is showing that you only have a single physical CPU with 2 cores.  I'm fairly sure that Atom CPUs lack the hardware needed to be placed in a multi-socket board.

---

### Post by J_Boner on 2010-08-14
Oh, I am very certain this has 2 atoms in it. Under windows 7 it read 4 cores, under fedora 12/13 it read 4 cores. I am very certain this puppy has 2 atoms w/ 2 cores a piece.

---

### Post by J_Boner on 2010-08-14
Ok,This is one of those times where I have to close this thread and explain what happened. Some how, hyper-threading was switched off in bios. Once hyper-threading was re-enabled:


processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping	: 2
cpu MHz		: 1599.855
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips	: 3199.71
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping	: 2
cpu MHz		: 1599.855
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 2
apicid		: 2
initial apicid	: 2
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips	: 3200.10
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping	: 2
cpu MHz		: 1599.855
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips	: 3200.00
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 28
model name	: Intel(R) Atom(TM) CPU  330   @ 1.60GHz
stepping	: 2
cpu MHz		: 1599.855
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 2
apicid		: 3
initial apicid	: 3
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de tsc msr pae mce cx8 apic mtrr pge mca cmov pat clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx lm constant_tsc arch_perfmon pebs bts aperfmperf pni dtes64 monitor ds_cpl tm2 ssse3 cx16 xtpr pdcm movbe lahf_lm
bogomips	: 3200.04
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 48 bits virtual
power management:

[IMG]http://farm5.static.flickr.com/4100/4890833011_c5ab6e1903_z.jpg[/IMG]

---

### Post by Zeike on 2010-08-14
Hyper threading makes each individual core appear as 2 to the operating system.  You only actually have 2 physical cores.

---

### Post by cascade9 on 2010-08-15
> **Zeike said:**
> Hyper threading makes each individual core appear as 2 to the operating system.  You only actually have 2 physical cores.

+1. 

Hyperthreading =/= extra cores.

---

### Post by SR_ELPIRATA on 2010-12-23
Definitely only 1 physical cpu with 2 individual cores :) This also happens with the P4's with hyperthreading, one processor which shows 2 pseudo cores.

---

