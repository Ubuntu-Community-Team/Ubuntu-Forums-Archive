---
title: "What Motherboard is this?"
date: 2008-12-18
forum: Hardware
---

### Post by HappyHenry on 2008-12-18
Hi
I have been running in circles for a couple days, trying to discover my motherboard model. I want to flash the bios. I can download the latest bios from HP but dont want anything from them I can get elsewhere. I would prefer to download the most current bios from the Intel folks but am not sure of my Motherboard.
lshu states: henry@henry-laptop:~$ lshw
WARNING: you should run this program as super-user.
henry-laptop              
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 3026MiB
     *-cpu
          product: Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1801MHz
          capacity: 1801MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr lahf_lm ida cpufreq
          configuration: id=1
        *-logicalcpu:0
             description: Logical CPU
             physical id: 1.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 1.2
             width: 64 bits
             capabilities: logical
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp.....

and Sysinfo states: Host bridge is, Intel Corp Mobile PM965/gm965/gl960 mem control, Subsystem; Hewlett-Packard Company Compaq 6710b.....

Well I really dont want to pop it open to read what board it is. Yes a little too lazy.(after all the screwdriver is in the garage and its [COLOR="RoyalBlue"]winter[/COLOR]!) The crazy "bios" screen is modified by HP with all the HP logos and names for everything. _[COLOR="Red"]I would like to be sure of the board model and download the bios from Intel.[/COLOR]_ Is there a way to discover this or has paranoia/greed of HP left me no option but to brave the cold??? Thanks for any help anyone can share with me.

---

### Post by xjcannonx on 2008-12-18
```
sudo dmidecode | more
```

---

### Post by HappyHenry on 2008-12-18
Thank you. Wow, thats a lot of info. Theres nothing that says, "motherboard = intel_____" so im not sure where the motherboard info is in the list.
It's a big list, sorry I don't know what the pertinent info is, so I will have to post the whole thing;

# dmidecode 2.9
SMBIOS 2.4 present.
25 structures occupying 1236 bytes.
Table at 0x000F25BA.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Hewlett-Packard
	Version: 68DDU Ver. F.0B
	Release Date: 08/02/2007
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 1024 kB
	Characteristics:
		PCI is supported
		PC Card (PCMCIA) is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		3.5"/720 KB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		ACPI is supported
		USB legacy is supported
		LS-120 boot is supported
		Smart battery is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported
		Targeted content distribution is supported
	BIOS Revision: 15.11
	Firmware Revision: 113.42

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Hewlett-Packard
	Product Name: HP Compaq 6710b (GF938AT#ABA)
	Version: F.0B
	Serial Number: CNU73520RX
	UUID: 490A94FC-C315-E011-4094-6D990E3C7529
	Wake-up Type: Power Switch
	SKU Number: GF938AT#ABA
	Family: 103C_5336AN

Handle 0x0040, DMI type 126, 34 bytes
Inactive

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: Hewlett-Packard
	Product Name: 30C0
	Version: KBC Version 71.2A
	Serial Number: Not Specified

Handle 0x0003, DMI type 3, 13 bytes
Chassis Information
	Manufacturer: Hewlett-Packard
	Type: Notebook
	Lock: Not Present
	Version: Not Specified
	Serial Number: CNU73520RX
	Asset Tag: CNU73520RX
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: External Interface Enabled

Handle 0x0041, DMI type 126, 32 bytes
Inactive

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
	Socket Designation: U10
	Type: Central Processor
	Family: Pentium M
	Manufacturer: Intel(R)
	ID: FD 06 00 00 FF FB EB BF
	Signature: Type 0, Family 6, Model 15, Stepping 13
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
	Version: Intel(R) Core(TM)2 Duo CPU     T7100  @ 1.80GHz
	Voltage: 1.1 V
	External Clock: 200 MHz
	Max Speed: 1800 MHz
	Current Speed: 1800 MHz
	Status: Populated, Enabled
	Upgrade: None
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: Not Provided
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Internal L1 Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 64 KB
	Maximum Size: 64 KB
	Supported SRAM Types:
		Burst
	Installed SRAM Type: Burst
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unified
	Associativity: 4-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Internal L2 Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: External
	Installed Size: 2048 KB
	Maximum Size: 2048 KB
	Supported SRAM Types:
		Burst
	Installed SRAM Type: Burst
	Speed: Unknown
	Error Correction Type: None
	System Type: Unified
	Associativity: 4-way Set-associative

Handle 0x0007, DMI type 9, 13 bytes
System Slot Information
	Designation: PC CARD-Slot 0
	Type: 32-bit PC Card (PCMCIA)
	Current Usage: Available
	Length: Short
	ID: Adapter 0, Socket 0
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PC Card-16 is supported
		Cardbus is supported
		PME signal is supported

Handle 0x0008, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description: 8

Handle 0x0009, DMI type 11, 5 bytes
OEM Strings
	String 1: [www.hp.com](www.hp.com)
	String 2: ABS 70/71 79 7A 7B 7C

Handle 0x000A, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Error Information Handle: No Error
	Number Of Devices: 2

Handle 0x000B, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x000A
	Error Information Handle: No Error
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: SODIMM
	Set: None
	Locator: DIMM #1
	Bank Locator: Not Specified
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: 7F7F9E0000000000         
	Serial Number: 00000000
	Asset Tag: Not Specified
	Part Number: VS2GSDS667D2      

Handle 0x000C, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x000A
	Error Information Handle: No Error
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: SODIMM
	Set: None
	Locator: DIMM #2
	Bank Locator: Not Specified
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: 7F7F9E0000000000         
	Serial Number: 00000000
	Asset Tag: Not Specified
	Part Number: VS2GSDS667D2      

Handle 0x000D, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Physical Array Handle: 0x000A
	Partition Width: 0

Handle 0x000E, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x000B
	Memory Array Mapped Address Handle: 0x000D
	Partition Row Position: 1

Handle 0x000F, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00080000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x000C
	Memory Array Mapped Address Handle: 0x000D
	Partition Row Position: 2

Handle 0x0010, DMI type 22, 26 bytes
Portable Battery
	Location: Primary
	Manufacturer: Hewlett-Packard
	Manufacture Date: 08/01/2007
	Serial Number: 00538       
	Name: HP                
	Chemistry: Lithium Ion
	Design Capacity: 51000 mWh
	Design Voltage: 10800 mV
	SBDS Version: Not Specified
	Maximum Error: Unknown
	OEM-specific Information: 0x00000000

Handle 0x0011, DMI type 126, 26 bytes
Inactive

Handle 0x0012, DMI type 32, 11 bytes
System Boot Information
	Status: No errors detected

Handle 0x0085, DMI type 133, 34 bytes
OEM-specific Type
	Header and Data:
		85 22 85 00 01 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 02 00 00 00 00 00 00 00 00
		00 00
	Strings:
		                
		No battery        

Handle 0x0086, DMI type 134, 34 bytes
OEM-specific Type
	Header and Data:
		86 22 86 00 01 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 00 00 02 00 00 00 00 00 00 00 00
		00 00
	Strings:
		                
		                  

Handle 0x0013, DMI type 144, 26 bytes
OEM-specific Type
	Header and Data:
		90 1A 13 00 FF FF FF FF FF FF FF FF FF FF FF FF
		FF FF FF FF FF FF FF FF 00 00

Handle 0x0014, DMI type 127, 4 bytes
End Of Table
?????????????????????????????????????????????????????????????????/

---

### Post by xjcannonx on 2008-12-18
This is your mobo```
Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
Manufacturer: [COLOR="Blue"]Hewlett-Packard[/COLOR]
Product Name: [COLOR="Blue"]30C0[/COLOR]
Version: [COLOR="Blue"]KBC Version 71.2A[/COLOR]
Serial Number: Not Specified
```

---

### Post by HappyHenry on 2008-12-18
Thank you. Looks like they built the board huh? Rats I was thinking the board was actually built by another company and they just assembled and branded it there product. Okay, well, I guess I will use there bios update. argg. I had read that the chip for video could be set to a share a specific amount of memory if the bios for the board was flashed without the HP modifications to it. Now with the HP mods to the bios you can not changed the amount of memory the vid is supposed to use. Windows is supposed to control it.. Well, I dont want that.. Linux is what I am useing. Thank you again for showing me the information!

---

