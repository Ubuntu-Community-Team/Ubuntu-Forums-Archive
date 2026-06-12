---
title: "A CPU mystery"
date: 2012-06-29
forum: Hardware
---

### Post by unimatrix on 2012-06-29
I'm having lots of difficulties determining what CPU my server has. It is an IBM xSeries 225 (with [amazing specifications that tell you everything you need to know]("http://download.boulder.ibm.com/ibmdl/pub/systems/support/system_x_pdf/x225spec.pdf")).
All I know is that it is an "Intel Xeon 2.8GHz", but this does not tell me anything as there are hundreds of different Xeons.

I have done all the research I could, with no luck. I will post all the disposable data here and hope that somebody could help me resolve this mystery.

Obviously I started with */proc/cpuinfo*:
```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: _Intel(R) Xeon(TM) CPU 2.80GHz_
stepping	: 9
cpu MHz		: 2800.027
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
**apicid		: 0**
**initial apicid	: 0**
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss **ht** tm pbe pebs bts cid xtpr
bogomips	: 5600.05
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 15
model		: 2
model name	: _Intel(R) Xeon(TM) CPU 2.80GHz_
stepping	: 9
cpu MHz		: 2800.027
cache size	: 512 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 1
**apicid		: 1**
**initial apicid	: 1**
fdiv_bug	: no
hlt_bug		: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 2
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss **ht** tm pbe pebs bts cid xtpr
bogomips	: 5600.50
clflush size	: 64
cache_alignment	: 128
address sizes	: 36 bits physical, 32 bits virtual
power management:

```

So the first thing we notice that this is a dual core Intel Xeon. But not really. The "physical id" and "core id" are the same in both "CPUs".
What is different is the **apicid** (0 and 1). So what is APIC? A quick Google search reveals [this]("http://en.wikipedia.org/wiki/Advanced_Programmable_Interrupt_Controller").
What does this mean? Does it indicate Hyper-Threading? The CPU clearly supports it (see: **ht** flag).

Alright, so this didn't give me all the information I hoped for. Let's try *dmidecode -t processor*:

```

# dmidecode 2.9
SMBIOS 2.2 present.

Handle 0x0004, DMI type 4, 32 bytes
Processor Information
	Socket Designation: CPU1
	Type: Central Processor
	Family: Xeon
	Manufacturer: Intel
	ID: **29 0F 00 00 FF FB EB BF**
	Signature: Type 0, Family 15, Model 2, Stepping 9
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
	Version: Intel Xeon(tm)
	Voltage: 1.5 V
	External Clock: 133 MHz
	Max Speed: 3200 MHz
	Current Speed: 2800 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x000B
	L2 Cache Handle: 0x000D
	L3 Cache Handle: 0x000F

Handle 0x0005, DMI type 4, 32 bytes
Processor Information
	Socket Designation: CPU2
	Type: Central Processor
	Family: Xeon
	Manufacturer: Intel
	ID: **29 0F 00 00 FF FB EB BF**
	Signature: Type 0, Family 15, Model 2, Stepping 9
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
	Version: Intel Xeon(tm)
	Voltage: 1.5 V
	External Clock: 133 MHz
	Max Speed: 3200 MHz
	Current Speed: Unknown
	Status: **Populated, Disabled By User**
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x000C
	L2 Cache Handle: 0x000E
	L3 Cache Handle: 0x0010

```

Alright! There is an ID. Clearly I will be able to find out exactly which CPU this is right? Clearly Intel has a way to search for processors by their ID... Yeah right. Intel has never heard of their own product IDs. Their documentation website is less than useless. :-|

And what is this? The second CPU is showing "**Status: Populated, Disabled By User**". Disabled by user? How do I enable it? I never disabled anything! Are you telling me my box has two virtual or whatever CPUs, but is only using one?!? :x

We need to dig deeper. Let's ask *lshw -C cpu*:

```

  *-cpu:0                 
       description: CPU
       product: Intel(R) Xeon(TM) CPU 2.80GHz
       vendor: Intel Corp.
       physical id: 4
       bus info: cpu@0
       version: 15.2.9
       slot: CPU1
       size: 2800MHz
       capacity: 3200MHz
       width: 32 bits
       clock: 133MHz
       capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe pebs bts cid xtpr
       configuration: id=0
     *-logicalcpu:0
          description: Logical CPU
          physical id: 0.1
          width: 32 bits
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 0.2
          width: 32 bits
          capabilities: logical
  *-cpu:1 **DISABLED**
       description: CPU
       vendor: Intel
       physical id: 5
       bus info: cpu@1
       version: 15.2.9
       slot: CPU2
       size: 2800MHz
       capacity: 3200MHz
       clock: 133MHz
       capabilities: ht
       configuration: id=1
     *-logicalcpu:0
          description: Logical CPU
          physical id: 1.1
          capabilities: logical
     *-logicalcpu:1
          description: Logical CPU
          physical id: 1.2
          capabilities: logical
  *-processor **UNCLAIMED**
       description: SCSI Processor
       product: 02R0980a S320  1
       vendor: IBM
       physical id: 0.8.0
       bus info: scsi@4:0.8.0
       version: 1
       serial: 1
       configuration: ansiversion=2

```

Alright, this is getting more and more confusing. So apparently now there are 2 CPUs and a "SCSI Processor" which is **UNCLAIMED**.
And of those two CPUs each have 2 "**logicalcpu**"s. But the second CPU is, again, **DISABLED**. So instead of using 4 logical CPUs I'm using only 2. This is very irritating. :mad:

Another thing we can try is *x86info*. Let's see what it tells us:

```

x86info v1.25.  Dave Jones 2001-2009
Feedback to <davej@redhat.com>.

Found 2 CPUs
MP Table:
#	APIC ID	Version	State		Family	Model	Step	Flags
#	 0	 0x11	 BSP, usable	 15	 2	 9	 0xfbff

--------------------------------------------------------------------------
CPU #1
EFamily: 0 EModel: 0 Family: 15 Model: 2 Stepping: 9
CPU Model: **Pentium 4 (Northwood) [D1]**
Processor name string: Intel(R) Xeon(TM) CPU 2.80GHz
Type: 0 (Original OEM)	Brand: 11 (Intel® Xeon processor)
Pentium 4 specific MSRs:
/dev/cpu/0/msr: No such file or directory

Number of cores per physical package=1
Number of logical processors per socket=2
Number of logical processors per core=2
APIC ID: 0x0	Package: 0  Core: 0   SMT ID 0
eax in: 0x00000000, eax = 00000002 ebx = 756e6547 ecx = 6c65746e edx = 49656e69
eax in: 0x00000001, eax = 00000f29 ebx = 0002080b ecx = 00004400 edx = bfebfbff
eax in: 0x00000002, eax = 665b5001 ebx = 00000000 ecx = 00000000 edx = 007b7040

eax in: 0x80000000, eax = 80000004 ebx = 00000000 ecx = 00000000 edx = 00000000
eax in: 0x80000001, eax = 00000000 ebx = 00000000 ecx = 00000000 edx = 00000000
eax in: 0x80000002, eax = 20202020 ebx = 20202020 ecx = 20202020 edx = 20202020
eax in: 0x80000003, eax = 6e492020 ebx = 286c6574 ecx = 58202952 edx = 286e6f65
eax in: 0x80000004, eax = 20294d54 ebx = 20555043 ecx = 30382e32 edx = 007a4847

Cache info
 Instruction trace cache: 12K uOps, 8-way associative.
 L1 Data cache: 8KB, sectored, 4-way associative. 64 byte line size.
 L2 cache: 512KB, sectored, 8-way associative. 64 byte line size.
TLB info
 Instruction TLB: 4K, 2MB or 4MB pages, fully associative, 64 entries.
 Data TLB: 4KB or 4MB pages, fully associative, 64 entries.
Feature flags:
 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflsh ds acpi mmx fxsr sse sse2 ss ht tm pbe
Extended feature flags:
 cntx-id xTPR

Connector type: **Socket478** (PGA478 Socket)

Datasheet: [http://developer.intel.com/design/pentium4/datashts/24988703.pdf](http://developer.intel.com/design/pentium4/datashts/24988703.pdf)
	[http://developer.intel.com/design/pentium4/datashts/29864304.pdf](http://developer.intel.com/design/pentium4/datashts/29864304.pdf)
Errata: [http://developer.intel.com/design/pentium4/specupdt/249199.htm](http://developer.intel.com/design/pentium4/specupdt/249199.htm)
2.80GHz processor (estimate).

--------------------------------------------------------------------------
CPU #2
EFamily: 0 EModel: 0 Family: 15 Model: 2 Stepping: 9
CPU Model: **Pentium 4 (Northwood) [D1]**
Processor name string: Intel(R) Xeon(TM) CPU 2.80GHz
Type: 0 (Original OEM)	Brand: 11 (Intel® Xeon processor)
Pentium 4 specific MSRs:

Number of cores per physical package=1
Number of logical processors per socket=2
Number of logical processors per core=2
APIC ID: 0x1	Package: 0  Core: 0   SMT ID 1
eax in: 0x00000000, eax = 00000002 ebx = 756e6547 ecx = 6c65746e edx = 49656e69
eax in: 0x00000001, eax = 00000f29 ebx = 0102080b ecx = 00004400 edx = bfebfbff
eax in: 0x00000002, eax = 665b5001 ebx = 00000000 ecx = 00000000 edx = 007b7040

eax in: 0x80000000, eax = 80000004 ebx = 00000000 ecx = 00000000 edx = 00000000
eax in: 0x80000001, eax = 00000000 ebx = 00000000 ecx = 00000000 edx = 00000000
eax in: 0x80000002, eax = 20202020 ebx = 20202020 ecx = 20202020 edx = 20202020
eax in: 0x80000003, eax = 6e492020 ebx = 286c6574 ecx = 58202952 edx = 286e6f65
eax in: 0x80000004, eax = 20294d54 ebx = 20555043 ecx = 30382e32 edx = 007a4847

Cache info
 Instruction trace cache: 12K uOps, 8-way associative.
 L1 Data cache: 8KB, sectored, 4-way associative. 64 byte line size.
 L2 cache: 512KB, sectored, 8-way associative. 64 byte line size.
TLB info
 Instruction TLB: 4K, 2MB or 4MB pages, fully associative, 64 entries.
 Data TLB: 4KB or 4MB pages, fully associative, 64 entries.
Feature flags:
 fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflsh ds acpi mmx fxsr sse sse2 ss ht tm pbe
Extended feature flags:
 cntx-id xTPR

Connector type: **Socket478** (PGA478 Socket)

Datasheet: [http://developer.intel.com/design/pentium4/datashts/24988703.pdf](http://developer.intel.com/design/pentium4/datashts/24988703.pdf)
	[http://developer.intel.com/design/pentium4/datashts/29864304.pdf](http://developer.intel.com/design/pentium4/datashts/29864304.pdf)
Errata: [http://developer.intel.com/design/pentium4/specupdt/249199.htm](http://developer.intel.com/design/pentium4/specupdt/249199.htm)
2.80GHz processor (estimate).

--------------------------------------------------------------------------

```

Sweet! [Datasheet links]("http://developer.intel.com/design/pentium4/datashts/24988703.pdf")!
Oh wait... Intel removed them. ("He he, that will show those annoying customers trying to look up our product information!")

And apparently my Xeon has a 478 socket? :shock: WHAT? :confused: :mad: Xeons have 604 or LGA sockets!
Now suddenly there is talk about "Pentium 4 Northwood"? What the hell? How did we come from Xeon to P4?
What is this sorcery? What CPU is this?
Since when do Xeons have 478 sockets?
Do I have hyperthreading?
How many CPUs do I really have and why are half of them disabled?
What is going on in this machine? ](*,) :frown:

---

### Post by ahallubuntu on 2012-06-29
This might be helpful:

[http://en.wikipedia.org/wiki/List_of_Intel_Xeon_microprocessors](http://en.wikipedia.org/wiki/List_of_Intel_Xeon_microprocessors)

Search for "2800 MHz" and you find two CPUs with a D1 stepping and a 512KB cache: SL6WA (400MHZ FSB) or SL6VN and  SL6YQ (533MHZ FSB).  But I also see this line in one of your outputs:

clock: 133MHz

which means it is SL6VN or SL6YQ (533MHZ FSB) - basically just slight variations of the same CPU.

[http://ark.intel.com/products/27275/Intel-Xeon-Processor-2_80-GHz-512K-Cache-533-MHz-FSB](http://ark.intel.com/products/27275/Intel-Xeon-Processor-2_80-GHz-512K-Cache-533-MHz-FSB)

[http://www.cpu-world.com/sspec/SL/SL6VN.html](http://www.cpu-world.com/sspec/SL/SL6VN.html)

I take it the socket 478 annotation is just a mistake.

---

### Post by unimatrix on 2012-06-29
Well it could be that one... or not.
The first two CPUID words match (although they are reversed), but the FSB is wrong (which could just mean that it's running slower because of a poor chipset).
Also it does not support HyperThreading, which mine clearly does.

What if the 478 socket is not a mistake?
I found Intel also made a Pentium 4 called "Xeon" with 478 sockets and HyperThreading: [http://en.wikipedia.org/wiki/List_of_Intel_microprocessors#Xeon](http://en.wikipedia.org/wiki/List_of_Intel_microprocessors#Xeon)

What if it's this one:
[http://ark.intel.com/products/27495/Intel-Pentium-4-Processor-supporting-HT-Technology-2_80-GHz-512K-Cache-800-MHz-FSB](http://ark.intel.com/products/27495/Intel-Pentium-4-Processor-supporting-HT-Technology-2_80-GHz-512K-Cache-800-MHz-FSB)

---

### Post by ahallubuntu on 2012-06-29
> **unimatrix said:**
> Well it could be that one... or not.
The first two CPUID words match (although they are reversed)

Not reversed.  Hex numbers are  encoded LSB to MSB - the ID you show starts with 29 0F which is 0f29 as shown in one of the links.

> **unimatrix said:**
> but the FSB is wrong (which could just mean that it's running slower because of a poor chipset).

Your FSB is 533MHZ (133MHZ FSB clock x 4) which matches the CPU I posted.  

> **unimatrix said:**
> Also it does not support HyperThreading, which mine clearly does.

You're right about that - maybe there's a mistake somewhere.  The Wikipedia page also says that the Xeon 2.8B ( SL6VN or SL6YQ ) support HT.  Maybe Intel's page is mistaken.


> **unimatrix said:**
> What if the 478 socket is not a mistake?

I found Intel also made a Pentium 4 called "Xeon" with 478 sockets and HyperThreading: [http://en.wikipedia.org/wiki/List_of_Intel_microprocessors#Xeon](http://en.wikipedia.org/wiki/List_of_Intel_microprocessors#Xeon)


but that link also says "603 (OLGA 603)" not Socket 478

> **unimatrix said:**
> 
What if it's this one:
[http://ark.intel.com/products/27495/Intel-Pentium-4-Processor-supporting-HT-Technology-2_80-GHz-512K-Cache-800-MHz-FSB](http://ark.intel.com/products/27495/Intel-Pentium-4-Processor-supporting-HT-Technology-2_80-GHz-512K-Cache-800-MHz-FSB)

That one has an 800MHZ FSB and yours is only 533MHZ.

---

### Post by unimatrix on 2012-06-30
Alright, so is there a way to turn on HyperThreading and test if it really works?

---

### Post by ahallubuntu on 2012-06-30
If the CPU has hyperthreading, it should be on by default in Ubuntu.  I know whenever I've booted Ubuntu (a modern version, anyway, 10.04 LTS or newer) on a computer with hyperthreading that it simply shows a logical CPU for each thread.  On a P4 with hyperthreading, I'd see two logical CPUs.  That means Ubuntu is using hyperthreading.

---

### Post by Yellow Pasque on 2012-07-01
Make sure HT is turned on in BIOS.

---

