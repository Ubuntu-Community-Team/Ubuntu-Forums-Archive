---
title: "[SOLVED] Which Celeron model?"
date: 2008-10-12
forum: General Help
---

### Post by DougieFresh4U on 2008-10-12
I know that my machine is a DELL with an Intel motherboard and that it's a Celeron, but I need to know exactly what Celeron model it is.
Is there a code or some way to let me know? I know it's Celeron from the screen shot posted

---

### Post by Sam on 2008-10-12
```
cat /proc/cpuinfo
```

---

### Post by DougieFresh4U on 2008-10-12
> **Sam said:**
> ```
cat /proc/cpuinfo
```

Thanks, but that does not tell me 
```
#   Celeron (Willamette, Northwood, Celeron D)
# Celeron M
# Celeron (Coppermine, Tualatin)
```
Trying to get the proper Swiftfox file for my machine

---

### Post by Sam on 2008-10-12
Which "cpu family" and "model" does output the command I previously posted ?

---

### Post by Yellow Pasque on 2008-10-12
Post the output from that command. If it doesn't tell you, you can also try looking at Dell's site or perhaps dmidecode will give you more info:
```
sudo dmidecode -t 4
```

---

### Post by Yellow Pasque on 2008-10-12
Post the output from that command. If it doesn't tell you, you can also try looking at Dell's site or perhaps dmidecode will give you more info:
```
sudo dmidecode -t 4
```

---

### Post by DougieFresh4U on 2008-10-12
> **Sam said:**
> Which "cpu family" and "model" does output the command I previously posted ?

> **Temüjin said:**
> Post the output from that command. If it doesn't tell you, you can also try looking at Dell's site or perhaps dmidecode will give you more info:
```
sudo dmidecode -t 4
```

dougie@DougiesLeanMachine:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 4
model name	: Intel(R) Celeron(R) CPU 2.66GHz
stepping	: 1
cpu MHz		: 2659.955
cache size	: 256 KB
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe constant_tsc pebs bts pni monitor ds_cpl cid xtpr
bogomips	: 5319.91
clflush size	: 64
power management:

dougie@DougiesLeanMachine:~$ sudo dmidecode -t 4
# dmidecode 2.9
SMBIOS 2.3 present.

Handle 0x0400, DMI type 4, 32 bytes
Processor Information
	Socket Designation: Microprocessor
	Type: Central Processor
	Family: Pentium 4
	Manufacturer: Intel
	ID: 41 0F 00 00 FF FB EB BF
	Signature: Type 0, Family 15, Model 4, Stepping 1
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
		PSE-36 (36-bit page size extension)
		CLFSH (CLFLUSH instruction supported)
		DS (Debug store)
		ACPI (ACPI supported)
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Hyper-threading technology)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Not Specified
	Voltage: 1.1 V
	External Clock: 533 MHz
	Max Speed: 3600 MHz
	Current Speed: 2666 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x0700
	L2 Cache Handle: 0x0701
	L3 Cache Handle: Not Provided

---

### Post by Yellow Pasque on 2008-10-12
Pentium 4-based Celeron means you should get this Swiftfox
> #   Celeron (Willamette, Northwood, Celeron D)

---

### Post by DougieFresh4U on 2008-10-12
> **Temüjin said:**
> Pentium 4-based Celeron means you should get this Swiftfox

Thanks so much

---

