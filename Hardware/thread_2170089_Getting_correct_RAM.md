---
title: "Getting correct RAM"
date: 2013-08-24
forum: Hardware
---

### Post by cmcanulty on 2013-08-24
I have an HP 17" laptop model g72t-b60 it currently has 1 of 4gb of 2rx8 pc3-1006005-09-10-f2 and one empty slot and need a recommendation to add 4gb to it

---

### Post by Yellow Pasque on 2013-08-24
Get output of dmidecode to see what speed memory it is:
```
sudo apt-get install dmidecode
sudo dmidecode
```

---

### Post by cmcanulty on 2013-08-25
> **Temüjin said:**
> Get output of dmidecode to see what speed memory it is:
```
sudo apt-get install dmidecode
sudo dmidecode
```
ok thanks it gave a lot of output but don't see ram type
```
cmcanulty@darcytech:~$ sudo dmidecode
[sudo] password for cmcanulty: 
# dmidecode 2.11
SMBIOS 2.6 present.
30 structures occupying 1239 bytes.
Table at 0x000EA6F0.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Hewlett-Packard
	Version: F.46
	Release Date: 11/15/2010
	ROM Size: 2048 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
		Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
		5.25"/360 kB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 kB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		8042 keyboard services are supported (int 9h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 15.46
	Firmware Revision: 60.79

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Hewlett-Packard
	Product Name: HP G72                          
	Version: 04A7100000200000000020000
	Serial Number: 5CB10601BB
	UUID: Not Settable
	Wake-up Type: Power Switch
	SKU Number: XL280AV#ABA 
	Family: 103C_5335KV

Handle 0x0002, DMI type 2, 16 bytes
Base Board Information
	Manufacturer: Hewlett-Packard
	Product Name: 1439
	Version: 60.4F
	Serial Number: 5CB10601BB
	Asset Tag: Base Board Asset Tag
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Base Board Chassis Location
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0003, DMI type 3, 22 bytes
Chassis Information
	Manufacturer: Hewlett-Packard
	Type: Notebook
	Lock: Not Present
	Version: Chassis Version
	Serial Number: Chassis Serial Number
	Asset Tag: Chassis Asset Tag
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0
	SKU Number: Not Specified

Handle 0x0004, DMI type 9, 17 bytes
System Slot Information
	Designation: J5C1
	Type: x16 PCI Express x16
	Current Usage: Available
	Length: Other
	ID: 0
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1f.7

Handle 0x0005, DMI type 9, 17 bytes
System Slot Information
	Designation: J6C1
	Type: x1 PCI Express x1
	Current Usage: Available
	Length: Other
	ID: 0
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1f.7

Handle 0x0006, DMI type 9, 17 bytes
System Slot Information
	Designation: J6C2
	Type: x1 PCI Express x1
	Current Usage: Available
	Length: Other
	ID: 1
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1f.7

Handle 0x0007, DMI type 9, 17 bytes
System Slot Information
	Designation: J6D2
	Type: x1 PCI Express x1
	Current Usage: Available
	Length: Other
	ID: 2
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1f.7

Handle 0x0008, DMI type 9, 17 bytes
System Slot Information
	Designation: J7C1
	Type: x1 PCI Express x1
	Current Usage: Available
	Length: Other
	ID: 3
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1f.7

Handle 0x0009, DMI type 9, 17 bytes
System Slot Information
	Designation: J7D2
	Type: x1 PCI Express x1
	Current Usage: Available
	Length: Other
	ID: 4
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1f.7

Handle 0x000A, DMI type 9, 17 bytes
System Slot Information
	Designation: J8C2
	Type: x16 PCI Express x16
	Current Usage: Available
	Length: Other
	ID: 1
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1f.7

Handle 0x000B, DMI type 9, 17 bytes
System Slot Information
	Designation: J8C1
	Type: x1 PCI Express x1
	Current Usage: Available
	Length: Other
	ID: 5
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1f.7

Handle 0x000C, DMI type 11, 5 bytes
OEM Strings
	String 1: $HP$
	String 2: LOC#ABA
	String 3: ABS 70/71 79 7A 7B 7C
	String 4: CNB1 04A7100000200000000020000

Handle 0x000D, DMI type 21, 7 bytes
Built-in Pointing Device
	Type: Touch Pad
	Interface: PS/2
	Buttons: 4

Handle 0x000E, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x000F, DMI type 41, 11 bytes
Onboard Device
	Reference Designation: Video Graphics Controller
	Type: Video
	Status: Disabled
	Type Instance: 0
	Bus Address: 0001:7f:1f.7

Handle 0x0010, DMI type 41, 11 bytes
Onboard Device
	Reference Designation: Realtek Lan Controller
	Type: Ethernet
	Status: Disabled
	Type Instance: 0
	Bus Address: 0001:7f:1f.7

Handle 0x0011, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 8 GB
	Error Information Handle: No Error
	Number Of Devices: 2

Handle 0x0012, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x0011
	Error Information Handle: 0x0013
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 4096 MB
	Form Factor: SODIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK 0
	Type: DDR3
	Type Detail: Synchronous
	Speed: 1067 MHz
	Manufacturer: Samsung
	Serial Number: 7920C84F
	Asset Tag: Unknown
	Part Number: M471B5273CH0-CH9  
	Rank: 2

Handle 0x0013, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x0014, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Physical Device Handle: 0x0012
	Memory Array Mapped Address Handle: 0x0017
	Partition Row Position: 1
	Interleave Position: 1
	Interleaved Data Depth: 1

Handle 0x0015, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x0011
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK 2
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Unknown
	Part Number: Not Specified
	Rank: Unknown

Handle 0x0016, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x0017, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Physical Array Handle: 0x0011
	Partition Width: 2

Handle 0x0018, DMI type 4, 42 bytes
Processor Information
	Socket Designation: CPU
	Type: Central Processor
	Family: Core i7
	Manufacturer: Intel(R) Corporation
	ID: 55 06 02 00 FF FB EB BF
	Signature: Type 0, Family 6, Model 37, Stepping 5
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
		FXSR (FXSAVE and FXSTOR instructions supported)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Multi-threading)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Intel(R) Core(TM) i3 CPU       M 370  @ 2.40GHz
	Voltage: 0.0 V
	External Clock: 1066 MHz
	Max Speed: 2400 MHz
	Current Speed: 2400 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x001C
	L2 Cache Handle: 0x001B
	L3 Cache Handle: 0x0019
	Serial Number: Not Specified
	Asset Tag: FFFF
	Part Number: Not Specified
	Core Count: 2
	Core Enabled: 2
	Thread Count: 4
	Characteristics:
		64-bit capable

Handle 0x0019, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L3 Cache
	Configuration: Enabled, Not Socketed, Level 3
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 3072 kB
	Maximum Size: 3072 kB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: Other

Handle 0x001A, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 32 kB
	Maximum Size: 32 kB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Data
	Associativity: 8-way Set-associative

Handle 0x001B, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2 Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 256 kB
	Maximum Size: 256 kB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 8-way Set-associative

Handle 0x001C, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 32 kB
	Maximum Size: 32 kB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Instruction
	Associativity: 4-way Set-associative

Handle 0x001D, DMI type 127, 4 bytes
End Of Table

cmcanulty@darcytech:~$ 
```

---

### Post by Yellow Pasque on 2013-08-25
```
Handle 0x0012, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x0011
	Error Information Handle: 0x0013
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 4096 MB
	Form Factor: SODIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK 0
	Type: DDR3
	Type Detail: Synchronous
	Speed: 1067 MHz
	Manufacturer: Samsung
	Serial Number: 7920C84F
	Asset Tag: Unknown
	Part Number: M471B5273CH0-CH9 
```

It's a DDR3 SODIMM, and googling the part number shows it's rated at PC10600(1333MHz). Any SODIMM that matches those specs should work, for example, [http://www.newegg.com/Product/Product.aspx?Item=N82E16820231341](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231341)
Or if you want the exact same part number: [http://www.superbiiz.com/detail.php?name=D3-13S4GS1](http://www.superbiiz.com/detail.php?name=D3-13S4GS1)

---

### Post by cmcanulty on 2013-08-25
OK thanks!

---

### Post by varunendra on 2013-08-26
> **Temüjin said:**
> ```

	Type: DDR3
	Type Detail: Synchronous
	**Speed: [COLOR="#FF0000"]1067[/COLOR] MHz** 
```

It's a DDR3 SODIMM, and googling the part number shows it's rated at PC10600(**1333MHz**). Any SODIMM that matches those specs should work, for example, [http://www.newegg.com/Product/Product.aspx?Item=N82E16820231341](http://www.newegg.com/Product/Product.aspx?Item=N82E16820231341)

[s]But the currently installed one is 1066 MHz. Although a 1333 MHz module may work (if the controller supports it), it will work at 1066 MHz anyway to be able to work with the installed one.[/s] *[COLOR="#FF0000"]EDIT: Wrong assumption from the output. Thanks to Temüjin for correcting me.[/COLOR]* The safest option is to opt for the same module or at least a module with exactly the same frequency[s] - 1066 MHz.[/s]

By the way, the output of "dmidecode" can be limited to a particular type of dmi device by using "-t" option. For example -
```
sudo dmidecode -t memory
```

---

### Post by Yellow Pasque on 2013-08-26
> **varunendra said:**
> But the currently installed one is 1066 MHz.
If you look at the part number and google it, it's a 1333MHz module (I linked to it in my previous post).

---

### Post by varunendra on 2013-08-26
> **Temüjin said:**
> If you look at the part number and google it, it's a 1333MHz module (I linked to it in my previous post).

Yes, I just verified the part no. with Samsung's rating codes, and I stand corrected. It is indeed a 1333 MHz module.

I wonder if it is an underclocked bus causing it to operate at the lower speed. I have an Asus x54c, with a 2 GB onboard module, plus an additional 2 GB one that I upgraded to, and both show their standard speed - 1333 MHz -
```
Memory Device
	Array Handle: 0x003F
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: SODIMM
	Set: None
	Locator: ChannelA-DIMM0
	Bank Locator: BANK 0
	Type: DDR3
	Type Detail: Synchronous
	**Speed: 1333 MHz**
	Manufacturer: Hynix/Hyundai
	Serial Number: 00000000
	Asset Tag: 9876543210
	Part Number: HMT325S6CFR8C-H9  
	Rank: 1

Handle 0x0041, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x003F
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: SODIMM
	Set: None
	Locator: ChannelB-DIMM0
	Bank Locator: BANK 2
	Type: DDR3
	Type Detail: Synchronous
	**Speed: 1333 MHz**
	Manufacturer: Transcend
	Serial Number: 00095933
	Asset Tag: 9876543210
	Part Number: JM1333KSN-2G      
	Rank: 1
```

Thanks for correcting me Temüjin !

---

