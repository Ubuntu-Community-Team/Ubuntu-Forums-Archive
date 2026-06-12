---
title: "Incorrect CPU shown on T60p"
date: 2010-10-02
forum: Hardware
---

### Post by mengqing on 2010-10-02
Hi, I've got a Lenovo T60p 2007 model, and when I go to BIOS, I can see that the CPU is T2500 2Ghz

However in Ubuntu, if I open up the system monitoring, CPU is shown as Pentium M 756 1.6Ghz

I've also looked at /proc/cpuinfo and it is showing 756 as well..

Is there a patch or something for this CPU?

Thanks

---

### Post by IcarusR on 2010-10-03
You need to be running a SMP kernel. To check from a terminal run 

```
uname -a
```

If it has 'SMP' in it then it should run dual core ok. ON my laptop I get..

```
2.6.32-25-generic #44-Ubuntu SMP Fri Sep 17 20:26:08 UTC 2010 i686 GNU/Linux
```

---

### Post by mengqing on 2010-10-03
it does have SMP on it

```

2.6.32-25-generic-pae #44-Ubuntu SMP Fri Sep 17 21:57:48 UTC 2010 i686 GNU/Linux

```

and this is what I got when I cat /proc/cpuinfo

```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 14
model name	: Intel(R) Pentium(R) M CPU        756  @ 1.66GHz
stepping	: 8
cpu MHz		: 1000.000
cache size	: 2048 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 10
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx constant_tsc up arch_perfmon bts aperfmperf pni monitor vmx est tm2 xtpr pdcm
bogomips	: 3324.97
clflush size	: 64
cache_alignment	: 64
address sizes	: 32 bits physical, 32 bits virtual
power management:

```

---

### Post by IcarusR on 2010-10-03
What does this give ? Queries bios.

```
sudo dmidecode

```

---

### Post by mengqing on 2010-10-03
```

Processor Information
	Socket Designation: None
	Type: Central Processor
	Family: Pentium M
	Manufacturer: GenuineIntel
	ID: E8 06 00 00 FF FB E9 AF
	Signature: Type 0, Family 6, Model 14, Stepping 8
	Flags:
		FPU (Floating-point unit on-chip)
		VME (Virtual mode extension)
		DE (Debugging extension)
		PSE (Page size extension)
		TSC (Time stamp counter)
		MSR (Model specific registers)
		PAE (Physical address extension)
		MCE (Machine check exception)
		CX8 (CMPXCHG8 instruction supported)
		APIC (On-chip APIC hardware supported)
		SEP (Fast system call)
		MTRR (Memory type range registers)
		PGE (Page global enable)
		MCA (Machine check architecture)
		CMOV (Conditional move instruction supported)
		PAT (Page attribute table)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Genuine Intel(R) CPU           
	Voltage: 1.4 V
	External Clock: 167 MHz
	Max Speed: 1667 MHz
	Current Speed: 1667 MHz
	Status: Populated, Enabled
	Upgrade: None
	L1 Cache Handle: 0x000A
	L2 Cache Handle: 0x000C
	L3 Cache Handle: Not Provided
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

```

I can't really remember what I got under Windows, I was wondering if there is a patch that need to be applied?

---

### Post by IcarusR on 2010-10-03
That's not good. 

Sorry don't know what to suggest.

---

### Post by IcarusR on 2010-10-03
You could try a different kernel... perhaps non pae, standard generic & see if that works.

---

### Post by cascade9 on 2010-10-03
Just out of intrest, do you get 2 cores or 1 in htop, etc? 

BTW, this doesnt help that much...but AFAIK T2500s should have SSE3. Its possible that your BIOS doesnt support the CPU properly (yes, I know, it should be a 'factory' install but it can happen)......or that your BIOS is hacked because there is a fake T2500 in there (yes, this has happened as well, far to much) or the old favourite-its been stollen and replaced by a techie/distruibutor/etc (and yes, this too has happened....) 

I'll see what else I can think of overnight. Hopefully no more 'that happens' stuff, something useful ;)

---

### Post by mengqing on 2010-10-04
Looks like I've being ripped off

I just updated the BIOS, and now in BIOS it shows as Pentium M 756, so previously I think it was hacked to show as T2500

---

### Post by IcarusR on 2010-10-04
Sorry to hear that, at least you got to the bottom of it.

Any chance of going back to where you got it from ?

---

### Post by cascade9 on 2010-10-04
> **mengqing said:**
> Looks like I've being ripped off

I just updated the BIOS, and now in BIOS it shows as Pentium M 756, so previously I think it was hacked to show as T2500

Seriously uncool. :( 

> **IcarusR said:**
> Sorry to hear that, at least you got to the bottom of it.

Any chance of going back to where you got it from ?

+1. I'd also hassle lenovo about this. ;)

---

