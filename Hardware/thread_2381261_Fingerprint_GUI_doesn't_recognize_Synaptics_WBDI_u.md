---
title: "Fingerprint GUI doesn't recognize Synaptics WBDI under Ubuntu 17.10"
date: 2017-12-28
forum: Hardware
---

### Post by helotbc-0 on 2017-12-28
I have just installed Ubuntu 17.10 on a Lenovo Yoga 720 and have installed Fingerprint GUI. Fingerprint GUI tells me "No devices detected":
[IMG]file:///home/brendan/Pictures/fingerprint.png[/IMG]

lsusb is
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 8087:0a2b Intel Corp. 
Bus 001 Device 003: ID 06cb:0081 Synaptics, Inc. 
Bus 001 Device 002: ID 13d3:5621 IMC Networks 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

system information is
BIOS Information
	Vendor: LENOVO
	Version: 1YCN36WW(V2.03)
	Release Date: 09/11/2017
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 6144 kB
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
		UEFI is supported
	BIOS Revision: 2.36
	Firmware Revision: 2.36


System Information
	Manufacturer: LENOVO
	Product Name: 81C3
	Version: Lenovo YOGA 720-13IKB
	Serial Number: MP1CHKDC
	UUID: CAF801D5-C387-11E7-BBB6-9829A61F3AF2
	Wake-up Type: Power Switch
	SKU Number: LENOVO_MT_81C3_BU_idea_FM_YOGA 720-13IKB
	Family: YOGA 720-13IKB


Base Board Information
	Manufacturer: LENOVO
	Product Name: LNVNB161216
	Version: SDK0J40709 WIN
	Serial Number: MP1CHKDC
	Asset Tag: NO Asset Tag
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Type2 - Board Chassis Location
	Type: Motherboard


Chassis Information
	Manufacturer: LENOVO
	Type: Convertible
	Lock: Not Present
	Version: Lenovo YOGA 720-13IKB
	Serial Number: MP1CHKDC
	Asset Tag: NO Asset Tag
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0
	SKU Number: SKU Number


Processor Information
	Socket Designation: U3E1
	Type: Central Processor
	Family: Core i5
	Manufacturer: Intel(R) Corporation
	ID: EA 06 08 00 FF FB EB BF
	Signature: Type 0, Family 6, Model 142, Stepping 10
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
	Version: Intel(R) Core(TM) i5-8250U CPU @ 1.60GHz
	Voltage: 0.9 V
	External Clock: 100 MHz
	Max Speed: 8300 MHz
	Current Speed: 2800 MHz
	Status: Populated, Enabled
	Upgrade: Socket BGA1356
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Part Number: To Be Filled By O.E.M.
	Core Count: 4
	Core Enabled: 4
	Thread Count: 8
	Characteristics:
		64-bit capable
		Multi-Core
		Hardware Thread
		Execute Protection
		Enhanced Virtualization
		Power/Performance Control


Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 256 kB
	Maximum Size: 256 kB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Parity
	System Type: Unified
	Associativity: 8-way Set-associative


Cache Information
	Socket Designation: L2 Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 1024 kB
	Maximum Size: 1024 kB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 4-way Set-associative


Cache Information
	Socket Designation: L3 Cache
	Configuration: Enabled, Not Socketed, Level 3
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 6144 kB
	Maximum Size: 6144 kB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Multi-bit ECC
	System Type: Unified
	Associativity: 12-way Set-associative


Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: Keyboard
	External Connector Type: PS/2
	Port Type: Keyboard Port


Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: Mouse
	External Connector Type: PS/2
	Port Type: Mouse Port


Port Connector Information
	Internal Reference Designator: J2A1
	Internal Connector Type: None
	External Reference Designator: TV OUT
	External Connector Type: Mini DIN
	Port Type: Video Port


Port Connector Information
	Internal Reference Designator: J2A2
	Internal Connector Type: None
	External Reference Designator: CRT
	External Connector Type: DB-15 female
	Port Type: Video Port


Port Connector Information
	Internal Reference Designator: J2A2
	Internal Connector Type: None
	External Reference Designator: COM 1
	External Connector Type: DB-9 male
	Port Type: Serial Port 16550A Compatible


Port Connector Information
	Internal Reference Designator: J3A1
	Internal Connector Type: None
	External Reference Designator: USB
	External Connector Type: Access Bus (USB)
	Port Type: USB


Port Connector Information
	Internal Reference Designator: J3A1
	Internal Connector Type: None
	External Reference Designator: USB
	External Connector Type: Access Bus (USB)
	Port Type: USB


Port Connector Information
	Internal Reference Designator: J3A1
	Internal Connector Type: None
	External Reference Designator: USB
	External Connector Type: Access Bus (USB)
	Port Type: USB


Port Connector Information
	Internal Reference Designator: J5A1
	Internal Connector Type: None
	External Reference Designator: USB
	External Connector Type: Access Bus (USB)
	Port Type: USB


Port Connector Information
	Internal Reference Designator: J5A1
	Internal Connector Type: None
	External Reference Designator: USB
	External Connector Type: Access Bus (USB)
	Port Type: USB


Port Connector Information
	Internal Reference Designator: J5A2
	Internal Connector Type: None
	External Reference Designator: USB
	External Connector Type: Access Bus (USB)
	Port Type: USB


Port Connector Information
	Internal Reference Designator: J5A1
	Internal Connector Type: None
	External Reference Designator: Network
	External Connector Type: RJ-45
	Port Type: Network Port


Port Connector Information
	Internal Reference Designator: J9G2
	Internal Connector Type: On Board Floppy
	External Reference Designator: OnBoard Floppy Type
	External Connector Type: None
	Port Type: Other


Port Connector Information
	Internal Reference Designator: J7J1
	Internal Connector Type: On Board IDE
	External Reference Designator: OnBoard Primary IDE
	External Connector Type: None
	Port Type: Other


Port Connector Information
	Internal Reference Designator: J30
	Internal Connector Type: None
	External Reference Designator: Microphone In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port


Port Connector Information
	Internal Reference Designator: J30
	Internal Connector Type: None
	External Reference Designator: Line In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port


Port Connector Information
	Internal Reference Designator: J30
	Internal Connector Type: None
	External Reference Designator: Speaker Out
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port


System Slot Information
	Designation: J6C1
	Type: x1 PCI Express x1
	Current Usage: Available
	Length: Other
	ID: 1
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1c.0


System Slot Information
	Designation: J6D2
	Type: x1 PCI Express x1
	Current Usage: Available
	Length: Other
	ID: 2
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1c.1


System Slot Information
	Designation: J7C1
	Type: x1 PCI Express x1
	Current Usage: Available
	Length: Other
	ID: 3
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1c.2


System Slot Information
	Designation: J7D1
	Type: x1 PCI Express x1
	Current Usage: Available
	Length: Other
	ID: 4
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1c.3


System Slot Information
	Designation: J8C1
	Type: x4 PCI Express x4
	Current Usage: Available
	Length: Other
	ID: 5
	Characteristics:
		PME signal is supported
		Hot-plug devices are supported
	Bus Address: 0000:00:1c.4


OEM Strings
	String 1: OemString1
	String 2: OemString2
	String 3: OemString3


System Configuration Options
	Option 1: ConfigOptions1
	Option 2: ConfigOptions2
	Option 3: ConfigOptions3


BIOS Language Information
	Language Description Format: Long
	Installable Languages: 8
		en|US|iso8859-1,0
		fr|FR|iso8859-1,0
		zh|TW|unicode,0
		ja|JP|unicode,0
		it|IT|iso8859-1,0
		es|ES|iso8859-1,0
		de|DE|iso8859-1,0
		pt|PT|iso8859-1,0
	Currently Installed Language: en|US|iso8859-1,0


Group Associations
	Name: Intel(R) Silicon View Technology
	Items: 1
		0x0040 (OEM-specific)


Group Associations
	Name: $MEI
	Items: 1
		0x003B (OEM-specific)


System Event Log
	Area Length: 0 bytes
	Header Start Offset: 0x0000
	Header Length: 8192 bytes
	Data Start Offset: 0x2000
	Access Method: General-purpose non-volatile data functions
	Access Address: 0x0000
	Status: Valid, Not Full
	Change Token: 0x12345678
	Header Format: OEM-specific
	Supported Log Type Descriptors: 3
	Descriptor 1: POST memory resize
	Data Format 1: None
	Descriptor 2: POST error
	Data Format 2: POST results bitmap
	Descriptor 3: Log area reset/cleared
	Data Format 3: None


Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 32 GB
	Number Of Devices: 2


Memory Device
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 4096 MB
	Form Factor: SODIMM
	Set: None
	Locator: ChannelA-DIMM0
	Bank Locator: BANK 0
	Type: DDR4
	Type Detail: Synchronous Unbuffered (Unregistered)
	Speed: 2400 MT/s
	Manufacturer: Samsung
	Serial Number: 00000000
	Asset Tag: 9876543210
	Part Number: M471A5244CB0-CRC    
	Rank: 1
	Configured Clock Speed: 2400 MT/s
	Minimum Voltage: 1.5 V
	Maximum Voltage: 1.5 V
	Configured Voltage: 1.2 V


Memory Device
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 4096 MB
	Form Factor: SODIMM
	Set: None
	Locator: ChannelB-DIMM0
	Bank Locator: BANK 2
	Type: DDR4
	Type Detail: Synchronous Unbuffered (Unregistered)
	Speed: 2400 MT/s
	Manufacturer: Samsung
	Serial Number: 00000000
	Asset Tag: 9876543210
	Part Number: M471A5244CB0-CRC    
	Rank: 1
	Configured Clock Speed: 2400 MT/s
	Minimum Voltage: 1.5 V
	Maximum Voltage: 1.5 V
	Configured Voltage: 1.2 V


Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x001FFFFFFFF
	Range Size: 8 GB
	Partition Width: 2


Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Partition Row Position: Unknown
	Interleave Position: 1
	Interleaved Data Depth: 1


Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Partition Row Position: Unknown
	Interleave Position: 2
	Interleaved Data Depth: 1


Built-in Pointing Device
	Type: Touch Pad
	Interface: PS/2
	Buttons: 4


Portable Battery
	Location: Fake
	Manufacturer: -Virtual Battery 0-
	Manufacture Date: 08/08/2010
	Serial Number: Battery 0
	Name: CRB Battery 0
	Chemistry: Zinc Air
	Design Capacity: Unknown
	Design Voltage: Unknown
	SBDS Version: Not Specified
	Maximum Error: Unknown
	OEM-specific Information: 0x00000000


Hardware Security
	Power-On Password Status: Disabled
	Keyboard Password Status: Disabled
	Administrator Password Status: Disabled
	Front Panel Reset Status: Disabled


Voltage Probe
	Description: Voltage Probe Description
	Location: Unknown
	Status: Unknown
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00008000
	Nominal Value: 0.000 V


Cooling Device
	Type: Fan
	Status: OK
	OEM-specific Information: 0x00000000
	Nominal Speed: 8192 rpm
	Description: Cooling Device Description


Temperature Probe
	Description: Temperature Probe Description
	Location: Unknown
	Status: Unknown
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00008000
	Nominal Value: 0.0 deg C


System Boot Information
	Status: No errors detected


System Power Supply
	Location: OEM Define 0
	Name: OEM Define 1
	Manufacturer: OEM Define 2
	Serial Number: OEM Define 3
	Asset Tag: OEM Define 4
	Model Part Number: OEM Define 5
	Revision: OEM Define 6
	Max Power Capacity: 75 W
	Status: Not Present
	Type: Regulator
	Input Voltage Range Switching: Auto-switch
	Plugged: No
	Hot Replaceable: No


Onboard Device
	Reference Designation: IGD
	Type: Video
	Status: Disabled
	Type Instance: 1
	Bus Address: 0000:00:02.0

---

### Post by rubo77 on 2018-05-14
Did you find a solution?

---

### Post by QIII on 2018-05-14
@ rubo77 --

If you are having a similar issue, it would be best to start your own thread rather than tagging on to a thread that has been languishing for 6 months.  Apparently the OP was not interested in following this one up.

---

