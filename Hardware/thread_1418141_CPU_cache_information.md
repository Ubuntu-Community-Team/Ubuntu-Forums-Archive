---
title: "CPU cache information"
date: 2010-02-28
forum: Hardware
---

### Post by CHaoSlayeR on 2010-02-28
Hi there,

I just wanted to see if it is possible to get correct cache size information about the CPU(s) from within Linux.

So I first looked at /proc/cpuinfo which states:
```
processor	: 0
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Phenom(tm) II X4 955 Processor
stepping	: 3
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 4
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 6427.73
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 1
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Phenom(tm) II X4 955 Processor
stepping	: 3
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 4
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 6428.46
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 2
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Phenom(tm) II X4 955 Processor
stepping	: 3
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 3
cpu cores	: 4
apicid		: 2
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 6428.47
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate

processor	: 3
vendor_id	: AuthenticAMD
cpu family	: 16
model		: 4
model name	: AMD Phenom(tm) II X4 955 Processor
stepping	: 3
cpu MHz		: 800.000
cache size	: 512 KB
physical id	: 0
siblings	: 4
core id		: 2
cpu cores	: 4
apicid		: 3
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 5
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp lm 3dnowext 3dnow constant_tsc rep_good nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt
bogomips	: 6428.44
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 48 bits physical, 48 bits virtual
power management: ts ttp tm stc 100mhzsteps hwpstate


```

So the "cache size" entry seems to identify the Level 2 cache, but what about the others?

I then decided to have a look in the information that dmidecode provides:
```
# dmidecode 2.9
SMBIOS 2.4 present.
59 structures occupying 2921 bytes.
Table at 0x000F0100.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Award Software International, Inc.
	Version: F2
	Release Date: 12/03/2009
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 1024 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/360 KB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Targeted content distribution is supported

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Gigabyte Technology Co., Ltd.
	Product Name: GA-790XTA-UD4
	Version:  
	Serial Number:  
	UUID: 36434630-3439-3533-3433-3734FFFFFFFF
	Wake-up Type: Power Switch
	SKU Number:  
	Family:  

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: Gigabyte Technology Co., Ltd.
	Product Name: GA-790XTA-UD4
	Version: x.x
	Serial Number:  

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
	Manufacturer: Gigabyte Technology Co., Ltd.
	Type: Desktop
	Lock: Not Present
	Version:  
	Serial Number:  
	Asset Tag:  
	Boot-up State: Unknown
	Power Supply State: Unknown
	Thermal State: Unknown
	Security Status: Unknown
	OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
	Socket Designation: Socket M2
	Type: Central Processor
	Family: Athlon
	Manufacturer: AMD
	ID: 43 0F 10 00 FF FB 8B 17
	Signature: Family 16, Model 4, Stepping 3
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
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		HTT (Hyper-threading technology)
	Version: AMD Phenom(tm) II X4 955 Processor
	Voltage: 10.3 V
	External Clock: 200 MHz
	Max Speed: 3200 MHz
	Current Speed: 3200 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x000A
	L2 Cache Handle: 0x000C
	L3 Cache Handle: Not Provided
	Serial Number:  
	Asset Tag:  
	Part Number:  

Handle 0x0005, DMI type 5, 24 bytes
Memory Controller Information
	Error Detecting Method: 64-bit ECC
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 1024 MB
	Maximum Total Memory Size: 4096 MB
	Supported Speeds:
		70 ns
		60 ns
	Supported Memory Types:
		Standard
		EDO
	Memory Module Voltage: 3.3 V
	Associated Memory Slots: 4
		0x0006
		0x0007
		0x0008
		0x0009
	Enabled Error Correcting Capabilities:
		None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A0
	Bank Connections: 1
	Current Speed: 8 ns
	Type: Other Unknown EDO
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A1
	Bank Connections: 2
	Current Speed: 8 ns
	Type: Other Unknown EDO
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A2
	Bank Connections: 3
	Current Speed: 8 ns
	Type: Other Unknown EDO
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A3
	Bank Connections: 4
	Current Speed: 8 ns
	Type: Other Unknown EDO
	Installed Size: Not Installed
	Enabled Size: Not Installed
	Error Status: OK

Handle 0x000A, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Internal Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 128 KB
	Maximum Size: 128 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x000B, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Internal Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 128 KB
	Maximum Size: 128 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x000C, DMI type 7, 19 bytes
Cache Information
	Socket Designation: External Cache
	Configuration: Enabled, Not Socketed, Level 3
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 512 KB
	Maximum Size: 512 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x000D, DMI type 7, 19 bytes
Cache Information
	Socket Designation: External Cache
	Configuration: Disabled, Not Socketed, Level 2
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 0 KB
	Maximum Size: 1024 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: PRIMARY IDE
	Internal Connector Type: On Board IDE
	External Reference Designator:  
	External Connector Type: None
	Port Type: Other

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: FDD
	Internal Connector Type: On Board Floppy
	External Reference Designator:  
	External Connector Type: None
	Port Type: 8251 FIFO Compatible

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: COM1
	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
	External Reference Designator:  
	External Connector Type: DB-9 male
	Port Type: Serial Port 16450 Compatible

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: COM2
	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
	External Reference Designator:  
	External Connector Type: DB-9 male
	Port Type: Serial Port 16450 Compatible

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: LPT1
	Internal Connector Type: DB-25 female
	External Reference Designator:  
	External Connector Type: DB-25 female
	Port Type: Parallel Port ECP/EPP

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Keyboard
	Internal Connector Type: Other
	External Reference Designator:  
	External Connector Type: PS/2
	Port Type: Keyboard Port

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: PS/2 Mouse
	Internal Connector Type: PS/2
	External Reference Designator: Detected
	External Connector Type: PS/2
	Port Type: Mouse Port

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB
	Internal Connector Type: None
	External Reference Designator:  
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB
	Internal Connector Type: None
	External Reference Designator:  
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB
	Internal Connector Type: None
	External Reference Designator:  
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB
	Internal Connector Type: None
	External Reference Designator:  
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB
	Internal Connector Type: None
	External Reference Designator:  
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB
	Internal Connector Type: None
	External Reference Designator:  
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB
	Internal Connector Type: None
	External Reference Designator:  
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB
	Internal Connector Type: None
	External Reference Designator:  
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB
	Internal Connector Type: None
	External Reference Designator:  
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB
	Internal Connector Type: None
	External Reference Designator:  
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x001F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB
	Internal Connector Type: None
	External Reference Designator:  
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0020, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB
	Internal Connector Type: None
	External Reference Designator:  
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0021, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 7
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0022, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 6
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0023, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 8
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PME signal is supported
		SMBus signal is supported

Handle 0x0024, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express x16
	Type: x16 PCI Express
	Current Usage: Unknown
	Length: Other
	ID: 0
	Characteristics:
		3.3 V is provided

Handle 0x0025, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express x16
	Type: x16 PCI Express
	Current Usage: Unknown
	Length: Other
	ID: 0
	Characteristics:
		3.3 V is provided

Handle 0x0026, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express x1
	Type: x1 PCI Express
	Current Usage: Unknown
	Length: Other
	ID: 0
	Characteristics:
		3.3 V is provided

Handle 0x0027, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI Express x1
	Type: x1 PCI Express
	Current Usage: Unknown
	Length: Other
	ID: 0
	Characteristics:
		3.3 V is provided

Handle 0x0028, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 3
		n|US|iso8859-1
		n|US|iso8859-1
		r|CA|iso8859-1
	Currently Installed Language: n|US|iso8859-1

Handle 0x0029, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 16 GB
	Error Information Handle: Not Provided
	Number Of Devices: 4

Handle 0x002A, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0029
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: A0
	Bank Locator: Bank0/1
	Type: Unknown
	Type Detail: None
	Speed: 1800 MHz (0.6 ns)
	Manufacturer:  
	Serial Number:  
	Asset Tag:  
	Part Number:  

Handle 0x002B, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0029
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: A1
	Bank Locator: Bank2/3
	Type: Unknown
	Type Detail: None
	Speed: 1800 MHz (0.6 ns)
	Manufacturer:  
	Serial Number:  
	Asset Tag:  
	Part Number:  

Handle 0x002C, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0029
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: A2
	Bank Locator: Bank4/5
	Type: Unknown
	Type Detail: None
	Speed: 1800 MHz (0.6 ns)
	Manufacturer:  
	Serial Number:  
	Asset Tag:  
	Part Number:  

Handle 0x002D, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0029
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: A3
	Bank Locator: Bank6/7
	Type: Unknown
	Type Detail: None
	Speed: 1800 MHz (0.6 ns)
	Manufacturer:  
	Serial Number:  
	Asset Tag:  
	Part Number:  

Handle 0x002E, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Physical Array Handle: 0x0029
	Partition Width: 32

Handle 0x002F, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x002A
	Memory Array Mapped Address Handle: 0x002E
	Partition Row Position: 1

Handle 0x0030, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00080000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x002B
	Memory Array Mapped Address Handle: 0x002E
	Partition Row Position: 1

Handle 0x0031, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Device Handle: 0x002C
	Memory Array Mapped Address Handle: 0x002E
	Partition Row Position: 1

Handle 0x0032, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Device Handle: 0x002D
	Memory Array Mapped Address Handle: 0x002E
	Partition Row Position: 1

Handle 0x0033, DMI type 32, 11 bytes
System Boot Information
	Status: No errors detected

Handle 0x0034, DMI type 188, 212 bytes
OEM-specific Type
	Header and Data:
		BC D4 34 00 00 00 00 D0 00 00 00 00 00 00 00 30
		01 00 00 00 00 06 76 00 00 00 00 00 08 00 00 00
		00 40 58 40 00 00 01 00 03 00 00 00 00 00 2F 01
		00 00 00 00 01 00 00 00 00 00 00 00 02 00 00 00
		00 00 00 00 03 00 00 00 00 00 00 00 04 00 00 00
		00 00 00 00 05 00 00 00 00 00 00 00 06 00 00 00
		00 00 00 00 07 00 00 00 03 30 00 D0 01 00 00 00
		09 01 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 E0 3E 78 00
		00 00 00 00 00 00 00 00 00 00 00 00 06 00 88 0D
		28 00 11 18 05 00 00 00 D4 00 24 00 45 96 16 EB
		55 79 22 00 00 00 01 00 00 02 00 00 40 00 00 00
		5C 00 B0 4A 0D 09 48 3F 00 00 00 00 00 00 00 00
		00 00 00 00

Handle 0x0035, DMI type 190, 212 bytes
OEM-specific Type
	Header and Data:
		BE D4 35 00 C4 05 00 00 00 00 00 00 24 A4 40 04
		FB 0F E0 2C 01 00 00 00 09 01 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 E0 3E 78 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 06 02 88 0D
		28 00 11 18 00 00 00 00 25 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 25 00 00 00 00 00 00 00
		24 A4 40 04 FB 0F E0 2C 01 01 00 00 04 9F F7 01
		00 02 00 00 00 00 00 00 40 00 00 00 05 00 00 00
		D4 00 24 00 45 96 16 EB 55 69 22 00 00 00 01 00
		0D 09 48 3F 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00

Handle 0x0036, DMI type 192, 244 bytes
OEM-specific Type
	Header and Data:
		C0 F4 36 00 06 40 00 00 22 22 11 20 E7 88 71 0E
		FC 0A 0C 00 00 00 36 00 22 22 11 20 18 22 28 2D
		18 02 08 0D 34 38 40 42 14 18 00 02 30 00 00 00
		36 00 0A 0A 06 0A 0A 0A 06 0A 0C 08 0C 0C 0C 08
		0C 0C 0A 00 35 58 71 07 FC 0A 0C 00 00 00 00 00
		89 00 8D 00 91 00 94 00 98 00 09 00 0D 00 11 00
		14 00 00 00 09 00 0D 00 11 00 14 00 00 00 09 00
		0D 00 11 00 14 00 00 00 9B 00 A4 00 AD 00 B8 00
		1B 00 04 00 0D 00 18 00 1B 00 04 00 0D 00 18 00
		1B 00 04 00 0D 00 18 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00

Handle 0x0037, DMI type 194, 244 bytes
OEM-specific Type
	Header and Data:
		C2 F4 37 00 06 40 00 00 22 32 11 20 E7 88 71 0E
		FC 0A 0C 00 00 00 36 00 22 32 11 20 14 21 28 2C
		14 01 08 0C 32 36 3E 3F 12 16 1E 1F 2F 00 00 00
		36 00 0E 0E 0E 08 0E 0E 0E 08 0C 0C 0E 10 0C 0C
		0E 10 0A 00 09 16 00 01 FC 0A 0C 00 00 00 00 00
		90 00 91 00 93 00 99 00 9E 00 10 00 11 00 13 00
		19 00 00 00 10 00 11 00 13 00 19 00 00 00 10 00
		11 00 13 00 19 00 00 00 A3 00 AB 00 B5 00 BD 00
		03 00 0B 00 15 00 1D 00 03 00 0B 00 15 00 1D 00
		03 00 0B 00 15 00 1D 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00

Handle 0x0038, DMI type 196, 244 bytes
OEM-specific Type
	Header and Data:
		C4 F4 38 00 06 40 00 00 0B 00 12 00 1B 00 20 00
		00 00 00 00 0B 00 12 00 1B 00 00 00 00 00 0B 00
		12 00 1B 00 00 00 00 00 00 00 0B 00 12 00 27 00
		2C 00 30 00 33 00 07 00 0C 00 10 00 13 00 07 00
		0C 00 10 00 13 00 07 00 0C 00 10 00 13 00 0B 12
		1B 20 27 2C 30 33 6D 00 00 00 0C 01 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00

Handle 0x0039, DMI type 198, 244 bytes
OEM-specific Type
	Header and Data:
		C6 F4 39 00 06 40 00 00 09 00 15 00 1C 00 20 00
		1E 00 00 00 09 00 15 00 1C 00 00 00 1E 00 09 00
		15 00 1C 00 00 00 1E 00 00 00 09 00 15 00 27 00
		2D 00 30 00 31 00 07 00 0D 00 10 00 11 00 07 00
		0D 00 10 00 11 00 07 00 0D 00 10 00 11 00 09 15
		1C 20 27 2D 30 31 5E 00 00 00 F3 01 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00

Handle 0x003A, DMI type 127, 4 bytes
End Of Table


```

This looks good in the first place. But taking a deeper look reveals that it doesn't even mention the level 3 cache which is 6 MB on this CPU (see here: [URL="http://www.amd.com/us/products/desktop/processors/phenom-ii/Pages/phenom-ii-model-number-comparison.aspx"]AMD Phenom™ II Processor Model Number and Feature Comparisons
[/URL]). Also the level 2 cache information is somewhat misleading. One could think it is the overall level 2 cache size but it is per core and so should either be listed 4 times or a total of 2 MB. The level 1 cache is listed correctly here.

Does someone know how I can gather the information I need correctly?


Thanx,

C]-[aoZ

---

### Post by CHaoSlayeR on 2010-03-08
Ha! Found something that suites my needs:
```
lscpu
```

Output from a Phenom II X4 955 (3.2 GHz):
```
Architecture:          x86_64
CPU op-mode(s):        64-bit
CPU(s):                4
Thread(s) per core:    1
Core(s) per socket:    4
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            16
Model:                 4
Stepping:              3
CPU MHz:               800.000
Virtualization:        AMD-V
L1d cache:             64K
L1i cache:             64K
L2 cache:              512K
L3 cache:              6144K
```

Output from a AMD Athlon II X4 620 (2.6 GHz):
```
Architecture:          x86_64
CPU(s):                4
Thread(s) per core:    1
Core(s) per socket:    4
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            16
Model:                 5
Stepping:              2
CPU MHz:               800.000
Virtualization:        AMD-V
L1d cache:             64K
L1i cache:             64K
L2 cache:              512K
```

Now I only miss two things:

First, the real maximum configured speed of the processors like dmidecode give them:
```
...
        Version: AMD Phenom(tm) II X4 955 Processor
        Voltage: 10.3 V
        External Clock: 200 MHz
        Max Speed: 3200 MHz
        Current Speed: 3200 MHz
...
```

...and second, the Level-2 cache is somewhat misleading, as the L2 cache is per core here (as it is with the L1 caches). On the other side e.g. the Intel Core 2 Quad includes only 2 L2 caches which are shared between both cores on a die (the Core 2 Quad is just 2x Dual-Core). I wonder how that is going to be displayed. I couldn't find a sample output on the net and I don't have access to such an intel system currently.

So maybe someone could post the output here for reference.

The 'lscpu' command is in the "linux-util" package since Ubuntu 9.10 Karmic Koala.

C]-[aoZ

---

### Post by CHaoSlayeR on 2010-03-09
Just to add another one.

Intel Core 2 Duo E4600 (2.4GHz)
```
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                2
Thread(s) per core:    1
Core(s) per socket:    2
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 15
Stepping:              13
CPU MHz:               1200.000
L1d cache:             32K
L1i cache:             32K
L2 cache:              2048K
```

---

### Post by CHaoSlayeR on 2010-03-11
Intel Xeon E5440 (2.83GHz)

```
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                8
Thread(s) per core:    1
Core(s) per socket:    4
CPU socket(s):         2
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 23
Stepping:              6
CPU MHz:               2833.341
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              6144K
```


Intel Core i7 920 (2.67GHz)
```
Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
CPU(s):                8
Thread(s) per core:    2
Core(s) per socket:    4
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             GenuineIntel
CPU family:            6
Model:                 26
Stepping:              5
CPU MHz:               1600.000
Virtualization:        VT-x
L1d cache:             32K
L1i cache:             32K
L2 cache:              256K
L3 cache:              8192K
```

---

### Post by sachin123 on 2012-11-02
It really helped.Thanks.

> **CHaoSlayeR said:**
> Ha! Found something that suites my needs:
```
lscpu
```

Output from a Phenom II X4 955 (3.2 GHz):
```
Architecture:          x86_64
CPU op-mode(s):        64-bit
CPU(s):                4
Thread(s) per core:    1
Core(s) per socket:    4
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            16
Model:                 4
Stepping:              3
CPU MHz:               800.000
Virtualization:        AMD-V
L1d cache:             64K
L1i cache:             64K
L2 cache:              512K
L3 cache:              6144K
```

Output from a AMD Athlon II X4 620 (2.6 GHz):
```
Architecture:          x86_64
CPU(s):                4
Thread(s) per core:    1
Core(s) per socket:    4
CPU socket(s):         1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            16
Model:                 5
Stepping:              2
CPU MHz:               800.000
Virtualization:        AMD-V
L1d cache:             64K
L1i cache:             64K
L2 cache:              512K
```

Now I only miss two things:

First, the real maximum configured speed of the processors like dmidecode give them:
```
...
        Version: AMD Phenom(tm) II X4 955 Processor
        Voltage: 10.3 V
        External Clock: 200 MHz
        Max Speed: 3200 MHz
        Current Speed: 3200 MHz
...
```

...and second, the Level-2 cache is somewhat misleading, as the L2 cache is per core here (as it is with the L1 caches). On the other side e.g. the Intel Core 2 Quad includes only 2 L2 caches which are shared between both cores on a die (the Core 2 Quad is just 2x Dual-Core). I wonder how that is going to be displayed. I couldn't find a sample output on the net and I don't have access to such an intel system currently.

So maybe someone could post the output here for reference.

The 'lscpu' command is in the "linux-util" package since Ubuntu 9.10 Karmic Koala.

C]-[aoZ

---

