---
title: "how to tell if I have SDRAM, DDR1, DDR2?"
date: 2010-01-30
forum: Hardware
---

### Post by Zorgoth on 2010-01-30
I have two desktops, both of which are old and need memory upgrades.  One of them has 1GB of memory and I want to upgrade it to 2 or 3, and the other is a real fossil and has 128 MB of memory.  I am hoping that both are DDR1 because then I could take the 1GB chip from the one computer and use it in the other.  They are from 2001 and 2003 respectively I believe.  How do I tell which kinds of memory each computer has and which kinds each is compatible with, preferably without opening the boxes?

---

### Post by PRC09 on 2010-01-30
If they are from a mainstream supplier such as HP,Dell and such usually the manufacture website will give you the specs for your model.

---

### Post by Janneman27 on 2010-01-30
If you still have windows installed and (sort-of) working, try installing CPU-z (google it). This gives detailed specs of all major hardware components.

Otherwise, use wikipedia or google (whichever you're more comfortable with) to find pictures of different RAM types and form-factors. There are distinct visual differences. Compare these pics to the actual RAM modules in your rig.

Enjoy!

---

### Post by howefield on 2010-01-30
Try this command in a terminal (Applications > Accessories > Terminal) 

```
sudo dmidecode 
```

Sift through the output.

---

### Post by Zorgoth on 2010-01-30
OK so the newer computer (whose model I'm unsure of) has DDR (so says CPU-z - thanks!) and as for the older one i'm unsure but maybe it is RDRAM?  I tried sudo dmidecode and got

```


# dmidecode 2.9
SMBIOS 2.3 present.
97 structures occupying 2982 bytes.
Table at 0x000F0450.

Handle 0xDA00, DMI type 218, 53 bytes
OEM-specific Type
	Header and Data:
		DA 35 00 DA B2 00 17 0B 0E 18 00 00 00 00 80 01
		00 00 00 02 80 01 00 00 00 00 A0 01 00 58 00 58
		00 01 00 59 00 59 00 01 00 05 80 05 80 01 00 FF
		FF 00 00 00 00

Handle 0xDA01, DMI type 218, 47 bytes
OEM-specific Type
	Header and Data:
		DA 2F 01 DA B2 00 17 0B 0E 18 00 00 00 20 F3 00
		00 00 00 10 F3 00 00 00 00 30 F3 00 00 11 F5 11
		F5 00 00 00 00 12 F5 00 00 FF FF 00 00 00 00

Handle 0xDA02, DMI type 218, 131 bytes
OEM-specific Type
	Header and Data:
		DA 83 02 DA B2 00 17 0B 0E 18 00 00 00 20 F4 00
		00 00 00 10 F4 00 00 00 00 30 F4 00 00 00 00 40
		F4 00 00 00 00 21 F4 00 00 00 00 11 F4 00 00 00
		00 31 F4 00 00 00 00 41 F4 00 00 00 00 22 F4 00
		00 00 00 12 F4 00 00 00 00 32 F4 00 00 00 00 23
		F4 00 00 00 00 13 F4 00 00 00 00 33 F4 00 00 00
		00 43 F4 00 00 00 00 24 F4 00 00 00 00 14 F4 00
		00 00 00 34 F4 00 00 00 00 44 F4 00 00 FF FF 00
		00 00 00

Handle 0xDA03, DMI type 218, 161 bytes
OEM-specific Type
	Header and Data:
		DA A1 03 DA B2 00 17 0B 0E 18 00 00 00 25 F4 00
		00 00 00 15 F4 00 00 00 00 35 F4 00 00 00 00 45
		F4 00 00 00 00 26 F4 00 00 00 00 16 F4 00 00 00
		00 36 F4 00 00 00 00 46 F4 00 00 00 00 27 F4 00
		00 00 00 17 F4 00 00 00 00 37 F4 00 00 00 00 47
		F4 00 00 00 00 28 F4 00 00 00 00 18 F4 00 00 00
		00 38 F4 00 00 00 00 48 F4 00 00 00 00 29 F4 00
		00 00 00 19 F4 00 00 00 00 39 F4 00 00 00 00 49
		F4 00 00 00 00 2A F4 00 00 00 00 1A F4 00 00 00
		00 3A F4 00 00 00 00 4A F4 00 00 FF FF 00 00 00
		00

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: Dell Computer Corporation
	Version: A09
	Release Date: 10/02/2001
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 512 kB
	Characteristics:
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
		5.25"/360 KB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		ACPI is supported
		USB legacy is supported
		AGP is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported

Handle 0x0100, DMI type 1, 25 bytes
System Information
	Manufacturer: Dell Computer Corporation
	Product Name: Dimension 8100               
	Version: Not Specified
	Serial Number: DELL 
	UUID: 44454C4C-00C7-1044-8045-80C04F4C4C20
	Wake-up Type: Power Switch

Handle 0x0200, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: Dell Computer Corporation
	Product Name: Dimension 8100               
	Version:    
	Serial Number:                     

Handle 0x0300, DMI type 3, 13 bytes
Chassis Information
	Manufacturer: Dell Computer Corporation
	Type: Mini Tower
	Lock: Not Present
	Version: Not Specified
	Serial Number: DELL 
	Asset Tag: Not Specified
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: Unknown

Handle 0x0400, DMI type 4, 32 bytes
Processor Information
	Socket Designation: Microprocessor
	Type: Central Processor
	Family: Pentium 4
	Manufacturer: Intel
	ID: 0A 0F 00 00 FF F9 EB 3F
	Signature: Type 0, Family 15, Model 0, Stepping 10
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
	Version: Not Specified
	Voltage: 1.7 V
	External Clock: 100 MHz
	Max Speed: 2000 MHz
	Current Speed: 1300 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x0700
	L2 Cache Handle: 0x0701
	L3 Cache Handle: Not Provided

Handle 0x0700, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Not Specified
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 8 KB
	Maximum Size: 8 KB
	Supported SRAM Types:
		Unknown
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Data
	Associativity: 4-way Set-associative

Handle 0x0701, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Not Specified
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Varies With Memory Address
	Location: Internal
	Installed Size: 256 KB
	Maximum Size: 256 KB
	Supported SRAM Types:
		Unknown
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unified
	Associativity: Other

Handle 0x0800, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: PARALLEL
	Internal Connector Type: None
	External Reference Designator: Not Specified
	External Connector Type: DB-25 female
	Port Type: Parallel Port PS/2

Handle 0x0801, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: SERIAL1
	Internal Connector Type: None
	External Reference Designator: Not Specified
	External Connector Type: DB-9 male
	Port Type: Serial Port 16550A Compatible

Handle 0x0802, DMI type 126, 9 bytes
Inactive

Handle 0x0803, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: KYBD
	Internal Connector Type: None
	External Reference Designator: Not Specified
	External Connector Type: PS/2
	Port Type: Keyboard Port

Handle 0x0804, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: MOUSE
	Internal Connector Type: None
	External Reference Designator: Not Specified
	External Connector Type: Mini DIN
	Port Type: Mouse Port

Handle 0x0805, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB1
	Internal Connector Type: None
	External Reference Designator: Not Specified
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0806, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB2
	Internal Connector Type: None
	External Reference Designator: Not Specified
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0807, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB3
	Internal Connector Type: None
	External Reference Designator: Not Specified
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0808, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: USB4
	Internal Connector Type: None
	External Reference Designator: Not Specified
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0809, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: ENET
	Internal Connector Type: None
	External Reference Designator: Not Specified
	External Connector Type: RJ-45
	Port Type: Network Port

Handle 0x080A, DMI type 126, 9 bytes
Inactive

Handle 0x080B, DMI type 126, 9 bytes
Inactive

Handle 0x080C, DMI type 126, 9 bytes
Inactive

Handle 0x0901, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI1
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 1
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PME signal is supported

Handle 0x0902, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI2
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 2
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PME signal is supported

Handle 0x0903, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI3
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 3
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PME signal is supported

Handle 0x0904, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI4
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 4
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PME signal is supported

Handle 0x0905, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI5
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 5
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PME signal is supported

Handle 0x0906, DMI type 126, 13 bytes
Inactive

Handle 0x0907, DMI type 126, 13 bytes
Inactive

Handle 0x0908, DMI type 126, 13 bytes
Inactive

Handle 0x0909, DMI type 126, 13 bytes
Inactive

Handle 0x090A, DMI type 9, 13 bytes
System Slot Information
	Designation: AGP1
	Type: 32-bit AGP 4x
	Current Usage: In Use
	Length: Long
	ID: 0
	Characteristics:
		PME signal is supported

Handle 0x0A01, DMI type 10, 6 bytes
On Board Device Information
	Type: Ethernet
	Status: Enabled
	Description: 3Com Fast EtherLink XL 10/100Mb TX

Handle 0x0A02, DMI type 126, 6 bytes
Inactive

Handle 0x0B00, DMI type 11, 5 bytes
OEM Strings
	String 1: www.dell.com

Handle 0x0D00, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

Handle 0x0E00, DMI type 126, 11 bytes
Inactive

Handle 0x0E01, DMI type 126, 11 bytes
Inactive

Handle 0x0E02, DMI type 126, 11 bytes
Inactive

Handle 0x0E03, DMI type 126, 11 bytes
Inactive

Handle 0x0F00, DMI type 15, 31 bytes
System Event Log
	Area Length: 2049 bytes
	Header Start Offset: 0x0000
	Header Length: 16 bytes
	Data Start Offset: 0x0010
	Access Method: Memory-mapped physical 32-bit address
	Access Address: 0xFFF82000
	Status: Valid, Not Full
	Change Token: 0x00000033
	Header Format: Type 1
	Supported Log Type Descriptors: 4
	Descriptor 1: POST error
	Data Format 1: POST results bitmap
	Descriptor 2: System limit exceeded
	Data Format 2: System management
	Descriptor 3: Log area reset/cleared
	Data Format 3: None
	Descriptor 4: Multi-bit ECC memory error
	Data Format 4: Handle

Handle 0x1000, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: Single-bit ECC
	Maximum Capacity: 2 GB
	Error Information Handle: No Error
	Number Of Devices: 4

Handle 0x1100, DMI type 17, 23 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: No Error
	Total Width: 16 bits
	Data Width: 16 bits
	Size: 64 MB
	Form Factor: RIMM
	Set: 1
	Locator: RIMM_1
	Bank Locator: Not Specified
	Type: RDRAM
	Type Detail: RAMBus
	Speed: 400 MHz (2.5 ns)

Handle 0x1101, DMI type 17, 23 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: No Error
	Total Width: 16 bits
	Data Width: 16 bits
	Size: 64 MB
	Form Factor: RIMM
	Set: 1
	Locator: RIMM_2
	Bank Locator: Not Specified
	Type: RDRAM
	Type Detail: RAMBus
	Speed: 400 MHz (2.5 ns)

Handle 0x1102, DMI type 17, 23 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: No Error
	Total Width: Unknown
	Data Width: 16 bits
	Size: No Module Installed
	Form Factor: RIMM
	Set: 2
	Locator: RIMM_3
	Bank Locator: Not Specified
	Type: RDRAM
	Type Detail: RAMBus
	Speed: 400 MHz (2.5 ns)

Handle 0x1103, DMI type 17, 23 bytes
Memory Device
	Array Handle: 0x1000
	Error Information Handle: No Error
	Total Width: Unknown
	Data Width: 16 bits
	Size: No Module Installed
	Form Factor: RIMM
	Set: 2
	Locator: RIMM_4
	Bank Locator: Not Specified
	Type: RDRAM
	Type Detail: RAMBus
	Speed: 400 MHz (2.5 ns)

Handle 0x1200, DMI type 126, 23 bytes
Inactive

Handle 0x1301, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x00007FFFFFF
	Range Size: 128 MB
	Physical Array Handle: 0x1000
	Partition Width: 0

Handle 0xDF02, DMI type 31, 28 bytes
Boot Integrity Services Entry Point

Handle 0x1402, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x00007FFFFFF
	Range Size: 128 MB
	Physical Device Handle: 0x1100
	Memory Array Mapped Address Handle: 0x1301
	Partition Row Position: 1
	Interleave Position: 1
	Interleaved Data Depth: 8

Handle 0x1403, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x00007FFFFFF
	Range Size: 128 MB
	Physical Device Handle: 0x1101
	Memory Array Mapped Address Handle: 0x1301
	Partition Row Position: 1
	Interleave Position: 2
	Interleaved Data Depth: 8

Handle 0x1404, DMI type 126, 19 bytes
Inactive

Handle 0x1405, DMI type 126, 19 bytes
Inactive

Handle 0x1800, DMI type 24, 5 bytes
Hardware Security
	Power-On Password Status: Enabled
	Keyboard Password Status: Not Implemented
	Administrator Password Status: Enabled
	Front Panel Reset Status: Enabled

Handle 0x1900, DMI type 25, 9 bytes
	System Power Controls
	Next Scheduled Power-on: *-* 00:00:00

Handle 0x1A00, DMI type 126, 20 bytes
Inactive

Handle 0x1A01, DMI type 126, 20 bytes
Inactive

Handle 0x1A03, DMI type 126, 20 bytes
Inactive

Handle 0x1A04, DMI type 126, 20 bytes
Inactive

Handle 0x1A05, DMI type 126, 20 bytes
Inactive

Handle 0x1A06, DMI type 126, 20 bytes
Inactive

Handle 0x1A07, DMI type 126, 20 bytes
Inactive

Handle 0x1A08, DMI type 126, 20 bytes
Inactive

Handle 0x1A09, DMI type 126, 20 bytes
Inactive

Handle 0x1A0A, DMI type 126, 20 bytes
Inactive

Handle 0x1B00, DMI type 27, 12 bytes
Cooling Device
	Type: Fan
	Status: OK
	OEM-specific Information: 0x0000DD01

Handle 0x1B01, DMI type 126, 12 bytes
Inactive

Handle 0x1C00, DMI type 126, 20 bytes
Inactive

Handle 0x1C02, DMI type 126, 20 bytes
Inactive

Handle 0x2000, DMI type 32, 11 bytes
System Boot Information
	Status: No errors detected

Handle 0x2500, DMI type 37, 13 bytes
Memory Channel
	Type: RamBus
	Maximal Load: 32
	Devices: 2
	Device 1 Load: 0
	Device 1 Handle: 0x1102
	Device 2 Load: 0
	Device 2 Handle: 0x2500

Handle 0x2501, DMI type 37, 13 bytes
Memory Channel
	Type: RamBus
	Maximal Load: 32
	Devices: 2
	Device 1 Load: 0
	Device 1 Handle: 0x1103
	Device 2 Load: 0
	Device 2 Handle: 0xD000

Handle 0xD000, DMI type 208, 10 bytes
OEM-specific Type
	Header and Data:
		D0 0A 00 D0 01 03 C7 00 00 00

Handle 0xD100, DMI type 209, 12 bytes
OEM-specific Type
	Header and Data:
		D1 0C 00 D1 78 03 07 03 04 0F 80 05

Handle 0xD200, DMI type 210, 12 bytes
OEM-specific Type
	Header and Data:
		D2 0C 00 D2 F8 03 04 03 06 80 04 05

Handle 0xD201, DMI type 126, 12 bytes
Inactive

Handle 0xD400, DMI type 212, 172 bytes
OEM-specific Type
	Header and Data:
		D4 AC 00 D4 70 00 71 00 00 10 2D 2E 42 00 11 FE
		01 43 00 11 FE 00 51 00 26 3F 00 52 00 26 3F 40
		53 00 26 3F 80 54 00 26 3F C0 0F 00 25 FC 00 10
		00 25 FC 01 11 00 25 FC 02 12 00 25 FC 03 00 00
		25 F3 00 00 00 25 F3 04 00 00 25 F3 08 00 00 25
		F3 0C 07 00 23 8F 00 08 00 23 F3 00 09 00 23 F3
		04 0A 00 23 F3 08 0B 00 23 8F 10 0C 00 23 8F 20
		0E 00 23 8F 30 0D 00 23 8C 40 03 00 11 7F 80 04
		00 11 7F 00 90 00 11 CF 00 91 00 11 CF 20 92 00
		11 CF 10 55 00 3A 9F 00 6D 00 3A 9F 20 8E 00 3A
		9F 40 8F 00 3A 9F 00 FF FF 00 00 00

Handle 0xD401, DMI type 212, 142 bytes
OEM-specific Type
	Header and Data:
		D4 8E 01 D4 70 00 71 00 03 40 59 6D 2D 00 59 FC
		02 2E 00 59 FC 00 6E 00 59 FC 01 28 00 59 3F 00
		29 00 59 3F 40 2A 00 59 3F 80 2B 00 5A 00 00 2C
		00 5B 00 00 5C 00 78 BF 40 5D 00 78 BF 00 04 80
		78 F5 0A 01 A0 78 F5 00 1C 00 55 FB 04 1D 00 55
		FB 00 19 00 55 E7 00 1A 00 55 E7 08 1B 00 55 E7
		10 1E 00 55 FD 00 50 00 55 FD 02 93 00 7B 7F 80
		94 00 7B 7F 00 23 00 55 7F 00 22 00 55 7F 80 00
		C0 5C 00 0A 03 C0 67 00 05 FF FF 00 00 00

Handle 0xDC00, DMI type 220, 22 bytes
OEM-specific Type
	Header and Data:
		DC 16 00 DC 20 F4 00 00 10 F4 00 00 00 00 30 F4
		40 F4 00 00 00 00

Handle 0xDC01, DMI type 220, 22 bytes
OEM-specific Type
	Header and Data:
		DC 16 01 DC 21 F4 00 00 11 F4 00 00 00 00 31 F4
		41 F4 00 00 00 00

Handle 0xDC02, DMI type 220, 22 bytes
OEM-specific Type
	Header and Data:
		DC 16 02 DC 22 F4 00 00 12 F4 00 00 00 00 32 F4
		00 00 00 00 00 00

Handle 0xDC03, DMI type 220, 22 bytes
OEM-specific Type
	Header and Data:
		DC 16 03 DC 23 F4 00 00 13 F4 00 00 00 00 33 F4
		43 F4 00 00 00 00

Handle 0xDC04, DMI type 220, 22 bytes
OEM-specific Type
	Header and Data:
		DC 16 04 DC 24 F4 00 00 14 F4 00 00 00 00 34 F4
		44 F4 00 00 00 00

Handle 0xDC05, DMI type 220, 22 bytes
OEM-specific Type
	Header and Data:
		DC 16 05 DC 25 F4 00 00 15 F4 00 00 00 00 35 F4
		45 F4 00 00 00 00

Handle 0xDC06, DMI type 220, 22 bytes
OEM-specific Type
	Header and Data:
		DC 16 06 DC 26 F4 00 00 16 F4 00 00 00 00 36 F4
		46 F4 00 00 00 00

Handle 0xDC07, DMI type 220, 22 bytes
OEM-specific Type
	Header and Data:
		DC 16 07 DC 27 F4 00 00 17 F4 00 00 00 00 37 F4
		47 F4 00 00 00 00

Handle 0xDC08, DMI type 220, 22 bytes
OEM-specific Type
	Header and Data:
		DC 16 08 DC 28 F4 00 00 18 F4 00 00 00 00 38 F4
		48 F4 00 00 00 00

Handle 0xDC09, DMI type 220, 22 bytes
OEM-specific Type
	Header and Data:
		DC 16 09 DC 29 F4 00 00 19 F4 00 00 00 00 39 F4
		49 F4 00 00 00 00

Handle 0xDC0A, DMI type 220, 22 bytes
OEM-specific Type
	Header and Data:
		DC 16 0A DC 2A F4 00 00 1A F4 00 00 00 00 3A F4
		4A F4 00 00 00 00

Handle 0xDC11, DMI type 220, 22 bytes
OEM-specific Type
	Header and Data:
		DC 16 11 DC 20 F3 00 00 10 F3 00 00 00 00 30 F3
		00 00 00 00 00 00

Handle 0xDD01, DMI type 221, 19 bytes
OEM-specific Type
	Header and Data:
		DD 13 01 DD 00 01 00 00 00 11 F5 00 00 00 00 00
		00 00 00

Handle 0xDD02, DMI type 221, 19 bytes
OEM-specific Type
	Header and Data:
		DD 13 02 DD 00 01 00 00 00 12 F5 00 00 00 00 00
		00 00 00

Handle 0xDE00, DMI type 222, 13 bytes
OEM-specific Type
	Header and Data:
		DE 0D 00 DE C1 01 FF FF 00 00 00 00 00

Handle 0xDF00, DMI type 223, 61 bytes
OEM-specific Type
	Header and Data:
		DF 3D 00 DF 0C 00 11 05 00 00 00 00 00 00 00 11
		00 00 00 01 11 98 00 00 00 00 00 00 00 06 1D 15
		00 02 11 FF FF FF FF FF FF FF FF FF FF FF FF 03
		11 FF FF FF FF FF FF FF FF FF FF FF FF

Handle 0x7F00, DMI type 127, 4 bytes
End Of Table


```

I assume this means i can't so what I want to do but just in case, is it possible that a Dell Dimension 8100 (model of my older computer) could take DDR and is it possible that a computer designed for DDR could take DDR2?

---

### Post by howefield on 2010-01-30
Looks like you have 4 slots that can each take one (up to) 512 meg stick, 2 gig total. But you might pay a premium for old stuff like that.


[http://support.dell.com/support/edocs/systems/dsleest/specs.htm#memory](http://support.dell.com/support/edocs/systems/dsleest/specs.htm#memory)

---

### Post by Zorgoth on 2010-01-30
OK is this the right stuff?

[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=320475426336&rvr_id=&crlp=1_263602_263622&UA=WXF%3F&GUID=bd1dedcc1220a02684e1e0c1ff899217&itemid=320475426336&ff4=263602_263622](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=320475426336&rvr_id=&crlp=1_263602_263622&UA=WXF%3F&GUID=bd1dedcc1220a02684e1e0c1ff899217&itemid=320475426336&ff4=263602_263622)

---

### Post by Zorgoth on 2010-01-30
And will any DDR chip work for the other computer or do I have to be careful?

---

### Post by howefield on 2010-01-30
I won't tell you what to buy, but I'd say you need PC-800 45 ns or faster, 16-bit, RDRAM in pairs.

There are memory modules for Dell Dimension 8100s on ebay. Prices don't seem to bad.

---

### Post by Zorgoth on 2010-01-30
[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=380201319430&rvr_id=&crlp=1_263602_263622&UA=WXF%3F&GUID=bd1dedcc1220a02684e1e0c1ff899217&itemid=380201319430&ff4=263602_263622](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=380201319430&rvr_id=&crlp=1_263602_263622&UA=WXF%3F&GUID=bd1dedcc1220a02684e1e0c1ff899217&itemid=380201319430&ff4=263602_263622)

How does this look for my computer.  I am really just looking for a computer that will run internet, word processing, and homework for my brother and on which I can teach him C++.  I am using Xubuntu 9.10 so I don't have huge resource requirements.

---

### Post by Zorgoth on 2010-01-30
Oh and what does this mean?

This RAM will NOT work on 533Mhz FSB.

Hope I'm OK there?

---

### Post by Zorgoth on 2010-01-30
OK I bought some RDRAM.  Thank you so much for your help howefield.  I still have some questions but I am opening another thread.

---

### Post by Yellow Pasque on 2010-01-31
> **Zorgoth said:**
> Oh and what does this mean? This RAM will NOT work on 533Mhz FSB.

It means it won't work on a system that has a base clock of 133MHz (Intel uses quad-pumping on their CPU's, so that's effectively a 533MHz FSB). Your system has a 100 MHz clock, so you're okay there.

Your other computer is older and probably doesn't have DDR. Most likely, it has PC-133 or similar. Be careful. Post the model info if you can.

---

