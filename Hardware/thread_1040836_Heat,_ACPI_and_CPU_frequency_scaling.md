---
title: "Heat, ACPI and CPU frequency scaling"
date: 2009-01-15
forum: Hardware
---

### Post by jdeeth on 2009-01-15
I'm in Intrepid, kernel is  2.6.27-11 and I seem to have a triple problem here. It all started when I had a sudden system shutdown due to overheat. The CPUs are  
Intel(R) Core(TM)2 Duo CPU     T7700  @ 2.40GHz

Heat is a recurring problem so I often use CPU frequency scaling to turn it down to 2.0. When I died I was at 2.4.

So on reboot I hung at

0.019850] ACPI: Checking initramfs for custom DSDT

I was able to reboot with acpi=off, but then when Gnome reloads I was informed : "CPU frequency scaling not supported". Which... means I'm running hot again.

The funny thing about the overheating is that it's -17 F here in Iowa, so I may just solve the problem by taking the laptop outside. But any suggestions that'll both help me fix my machine and avoid frostbite would be welcome.

---

### Post by jdeeth on 2009-01-16
Well... I never did manage to actually fix it, but some kernel updates came down the pipe and that took care of it. Reminder to self: Don't set cpu speed above 2.0Ghz.

---

### Post by bricedebrignaisplage on 2009-09-04
I am also having temperature issue. With my desktop, under hardy, using KDE. For the anecdote, I'm in Singapore, so temperature here is constantly above 30C. It might be an issue with my fan, but I'd like to give a try to frequency scaling before buying a new fan.

May I know how you scale frequency based on cpu temperature rules? I briefly tried to use cpufreqd but had no success with it. Maybe the first step is: how do I check whether my hardware / kernel supports frequency scaling?

below is the info from /proc/cpuinfo. For some reason that I don't understand it shows 2 CPUs. Further below is the output from lshw (Desktop, BIOS and CPU). What else could be useful?




$ cat /proc/cpuinfo
processor       : 0
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 9
cpu MHz         : 3000.379
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips        : 6007.96
clflush size    : 64

processor       : 1
vendor_id       : GenuineIntel
cpu family      : 15
model           : 2
model name      : Intel(R) Pentium(R) 4 CPU 3.00GHz
stepping        : 9
cpu MHz         : 3000.379
cache size      : 512 KB
physical id     : 0
siblings        : 2
core id         : 0
cpu cores       : 1
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
bogomips        : 6000.68
clflush size    : 64




product: MS-7104
vendor: MICRO-STAR INTERNATIONAL CO., LTD
version: 20A
width: 32 bits
capabilities:
	SMBIOS version 2.3,
	DMI version 2.3,
	SMP specification v1.1,
	Symmetric Multi-Processing
configuration:
	boot: normal
	chassis: desktop
	cpus: 1


vendor: Phoenix Technologies, LTD
version: 6.00 PG (02/22/2006)
size: 128KiB
capacity: 448KiB
capabilities:
	ISA bus,
	PCI bus,
	Plug-and-Play,
	Advanced Power Management,
	BIOS EEPROM can be upgraded,
	BIOS shadowing,
	ESCD,
	Booting from CD-ROM/DVD,
	Selectable boot path,
	BIOS ROM is socketed,
	Enhanced Disk Drive extensions,
	5.25" 360KB floppy,
	5.25" 1.2MB floppy,
	3.5" 720KB floppy,
	3.5" 2.88MB floppy,
	Print Screen key,
	i8042 keyboard controller,
	INT14 serial line control,
	INT17 printer control,
	INT10 CGA/Mono video,
	ACPI,
	USB legacy emulation,
	AGP,
	Booting from LS-120,
	Booting from ATAPI ZIP,
	BIOS boot specification




product: Intel(R) Pentium(R) 4 CPU 3.00GHz
vendor: Intel Corp.
bus info: cpu@0
version: 15.2.9
slot: Socket 478
size: 3GHz
width: 32 bits
clock: 200MHz
capabilities:
	boot processor,
	mathematical co-processor,
	FPU exceptions reporting,
	wp,
	virtual mode extensions,
	debugging extensions,
	page size extensions,
	time stamp counter,
	model-specific registers,
	4GB+ memory addressing (Physical Address Extension),
	machine check exceptions,
	compare and exchange 8-byte,
	on-chip advanced programmable interrupt controller (APIC),
	fast system calls,
	memory type range registers,
	page global enable,
	machine check architecture,
	conditional move instruction,
	page attribute table,
	36-bit page size extensions,
	clflush,
	debug trace and EMON store MSRs,
	thermal control (ACPI),
	multimedia extensions (MMX),
	fast floating point save/restore,
	streaming SIMD extensions (SSE),
	streaming SIMD extensions (SSE2),
	self-snoop,
	HyperThreading,
	thermal interrupt and status,
	pending break event,
	pebs,
	bts,
	cid,
	xtpr
configuration:
	id: 1

---

