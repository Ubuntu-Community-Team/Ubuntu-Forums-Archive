---
title: "noapic affect dual core detection?"
date: 2008-08-16
forum: Hardware
---

### Post by jasonkirk2006 on 2008-08-16
Hello,

I have a Dell XPS M1530 notebook. After installing Ubuntu Hardy 64-bit, i had some problems with the hardware. First of all wireless card (iwl3945) is said to be in deep sleep (in dmesg logs). Some of the threads advice to use noapic kernel option. I tried and managed to make wireless work. But now, i can only see one of the cores of the CPU. Here is the whole output of cat /proc/cpuinfo

	processor	: 0
	vendor_id	: GenuineIntel
	cpu family	: 6
	model		: 23
	model name	: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz
	stepping	: 6
	cpu MHz		: 2501.000
	cache size	: 6144 KB
	physical id	: 0
	siblings	: 1
	core id		: 0
	cpu cores	: 1
	fpu		: yes
	fpu_exception	: yes
	cpuid level	: 10
	wp		: yes
	flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc up arch_perfmon pebs bts rep_good pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr sse4_1 lahf_lm ida
	bogomips	: 4992.71
	clflush size	: 64
	cache_alignment	: 64
	address sizes	: 36 bits physical, 48 bits virtual
	power management:

Also, System Monitor only displays single CPU graph.

I am now using the updated kernel 2.6.24-19 (i have applied all the updates listed in the Update Manager) and wondering if this is the result of using noapic kernel option. If so, is there any way to avoid ignoring one of the cores?

Here is my hardware:

CPU : Intel Core2Duo T9300
Wireless : Intel PRO/Wireless 3945ABG
HDD : Toshiba 250 GB 5400 rpm

By the way I am also using i8042.nomux=1 kernel option to make my touchpad work.

One final note: I installed another linux (Pardus 2008, kernel version 2.6.25-14) and am using both noapic and i8042.nomux=1 kernel options with it. There is no single-core detection issue in Pardus.

---

