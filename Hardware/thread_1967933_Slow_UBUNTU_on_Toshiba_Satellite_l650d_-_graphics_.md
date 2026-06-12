---
title: "Slow UBUNTU on Toshiba Satellite l650d - graphics not working?"
date: 2012-04-28
forum: Hardware
---

### Post by dom1n1cus on 2012-04-28
Hello,
I've been on Ubuntu for some time and I can't get rid of a feeling it is slower than it should. I mean, my hardware specs are not that bad(AMD Athlon II Dual-Core P320, RAM 4GB, ATI Radeon HD4200 512MB) so it shouldn't take 20 seconds to load LibreOffice's Calc, should it? I'm suspecting my graphic driver is not doing its job, but I don't know much about this. There are two options in System > Drivers: one of them calls an error on activation and doesn't even start working and the other turns green and crazy things start happening (menus are cut 45 degrees, things disappearing and appearing again...) I was lucky to turn it off again. I am still on ubuntu 11.10 with Gnome-shell

This is part if the glxinfo output:
```
OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD RS880
OpenGL version string: 2.1 Mesa 7.11
OpenGL shading language version string: 1.20

```

lspci output here:
```
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (int gfx)
00:04.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0)
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 41)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
01:05.1 Audio device: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200]
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
08:00.0 Ethernet controller: Atheros Communications AR8152 v1.1 Fast Ethernet (rev c1)
```
glxinfo | grep rendering
```
direct rendering: Yes

```

sudo dmidecode output here:
```
SMBIOS 2.6 present.
48 structures occupying 1725 bytes.
Table at 0x000E8100.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Insyde Corp.
	Version: 1.40
	Release Date: 05/19/2010
	ROM Size: 2048 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		Japanese floppy for NEC 9800 1.2 MB is supported (int 13h)
		Japanese floppy for Toshiba 1.2 MB is supported (int 13h)
		5.25"/360 KB floppy services are supported (int 13h)
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 KB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		8042 keyboard services are supported (int 9h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		Targeted content distribution is supported
	BIOS Revision: 1.40
	Firmware Revision: 1.10

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: TOSHIBA
	Product Name: Satellite L650D
	Version: PSK1NE-001005CZ
	Serial Number: 6A134381Q
	UUID: 10DB37A0-679E-11DF-9D50-00266C683801
	Wake-up Type: Power Switch
	SKU Number: Danube
	Family: Type1Family

Handle 0x0002, DMI type 2, 16 bytes
Base Board Information
	Manufacturer: TOSHIBA
	Product Name: Portable PC
	Version: Base Board Version
	Serial Number: None
	Asset Tag: No Asset Tag
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Base Board Chassis Location
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0003, DMI type 3, 22 bytes
Chassis Information
	Manufacturer: AMD
	Type: Notebook
	Lock: Not Present
	Version: None
	Serial Number: None
	Asset Tag: No Asset Tag
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0

Handle 0x0004, DMI type 9, 17 bytes
System Slot Information
	Designation: J6C1
	Type: x16 <OUT OF SPEC>
	Current Usage: Available
	Length: Long
	Characteristics:
		3.3 V is provided
		PME signal is supported
		Hot-plug devices are supported

Handle 0x0005, DMI type 9, 17 bytes
System Slot Information
	Designation: J8C1
	Type: x1 <OUT OF SPEC>
	Current Usage: Available
	Length: Short
	Characteristics:
		3.3 V is provided
		PME signal is supported
		Hot-plug devices are supported

Handle 0x0006, DMI type 9, 17 bytes
System Slot Information
	Designation: J7C1
	Type: x1 <OUT OF SPEC>
	Current Usage: Available
	Length: Short
	Characteristics:
		3.3 V is provided
		PME signal is supported
		Hot-plug devices are supported

Handle 0x0007, DMI type 9, 17 bytes
System Slot Information
	Designation: J8D1
	Type: x1 <OUT OF SPEC>
	Current Usage: Available
	Length: Short
	Characteristics:
		3.3 V is provided
		PME signal is supported
		Hot-plug devices are supported

Handle 0x0008, DMI type 9, 17 bytes
System Slot Information
	Designation: J8B1
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 5
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		Cardbus is supported
		Modem ring resume is supported
		PME signal is supported
		SMBus signal is supported

Handle 0x0009, DMI type 11, 5 bytes
OEM Strings
	String 1: PSK1NE-001005CZ,R12996CZ
	String 2: UeVSzqRwRDHwY
	String 3: FWJeD2j9rO3yr
	String 4: wSWQmkBzRearl
	String 5:                                 

Handle 0x000A, DMI type 12, 5 bytes
System Configuration Options
	Option 1: NVR:00707902
	Option 2: DSN:5VE77FQC            
	Option 3: DSN:M471B5673FH0-CF8  92ACAD40 
	Option 4: DSN:340F2337

Handle 0x000B, DMI type 21, 7 bytes
Built-in Pointing Device
	Type: Touch Pad
	Interface: PS/2
	Buttons: 4

Handle 0x000C, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x000D, DMI type 129, 5 bytes
OEM-specific Type
	Header and Data:
		81 05 0D 00 4F
	Strings:
		em Test 1
		Oem Test 2

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: Keyboard
	External Connector Type: PS/2
	Port Type: Keyboard Port

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: Mouse
	External Connector Type: PS/2
	Port Type: Mouse Port

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A2
	Internal Connector Type: None
	External Reference Designator: COM 1
	External Connector Type: DB-9 male
	Port Type: Serial Port 16550A Compatible

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J3A1
	Internal Connector Type: None
	External Reference Designator: USB
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J3A1
	Internal Connector Type: None
	External Reference Designator: USB
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J3A1
	Internal Connector Type: None
	External Reference Designator: USB
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J5A1
	Internal Connector Type: None
	External Reference Designator: USB
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J5A1
	Internal Connector Type: None
	External Reference Designator: USB
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J5A1
	Internal Connector Type: None
	External Reference Designator: Network
	External Connector Type: RJ-45
	Port Type: Network Port

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9G2
	Internal Connector Type: On Board Floppy
	External Reference Designator: OnBoard Floppy Type
	External Connector Type: None
	Port Type: Other

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J7J1
	Internal Connector Type: On Board IDE
	External Reference Designator: OnBoard Primary IDE
	External Connector Type: None
	Port Type: Other

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A1
	Internal Connector Type: None
	External Reference Designator: TV OUT
	External Connector Type: Mini DIN
	Port Type: Video Port

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A2
	Internal Connector Type: None
	External Reference Designator: CRT
	External Connector Type: DB-15 female
	Port Type: Video Port

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J30
	Internal Connector Type: None
	External Reference Designator: Microphone In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J30
	Internal Connector Type: None
	External Reference Designator: Line In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J30
	Internal Connector Type: None
	External Reference Designator: Speaker Out
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port

Handle 0x001E, DMI type 40, 18 bytes
Unknown Type
	Header and Data:
		28 12 1E 00 02 06 04 00 05 01 AA 07 00 00 05 02
		DC 05
	Strings:
		PCIExpressx16
		Compiler Version: VC 9.0

Handle 0x001F, DMI type 41, 11 bytes
Unknown Type
	Header and Data:
		29 0B 1F 00 01 85 01 00 00 00 01
	Strings:
		82567LM Gigabit Network Connection

Handle 0x0020, DMI type 4, 42 bytes
Processor Information
	Socket Designation: Socket S1G4
	Type: Central Processor
	Family: <OUT OF SPEC>
	Manufacturer: AMD processor
	ID: 63 0F 10 00 FF FB 8B 17
	Version: AMD Athlon(tm) II P320 Dual-Core Processor
	Voltage: 1.1 V
	External Clock: 200 MHz
	Max Speed: 2100 MHz
	Current Speed: 2100 MHz
	Status: Populated, Enabled
	Upgrade: <OUT OF SPEC>
	L1 Cache Handle: 0x0021
	L2 Cache Handle: 0x0022
	L3 Cache Handle: Not Provided
	Serial Number: NotSupport
	Asset Tag: FFFF
	Part Number: FFFF
	Core Count: 192
	Core Enabled: 2
	Thread Count: 2
	Characteristics:
		64-bit capable

Handle 0x0021, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 256 KB
	Maximum Size: 256 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Multi-bit ECC
	System Type: Unified
	Associativity: 2-way Set-associative

Handle 0x0022, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2 Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 1024 KB
	Maximum Size: 1024 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Multi-bit ECC
	System Type: Unified
	Associativity: 16-way Set-associative

Handle 0x0023, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 8 GB
	Error Information Handle: No Error
	Number Of Devices: 2

Handle 0x0024, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x0023
	Error Information Handle: 0x0025
	Total Width: 64 bits
	Data Width: 8 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK0
	Type: <OUT OF SPEC>
	Type Detail: Synchronous
	Speed: 1066 MHz (0.9 ns)
	Manufacturer: Samsung
	Serial Number: 92ACAD40
	Asset Tag: Unknown
	Part Number: M471B5673FH0-CF8  

Handle 0x0025, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x0026, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM0
	Bank Connections: None
	Current Speed: Unknown
	Type: Unknown DIMM
	Installed Size: 2048 MB (Single-bank Connection)
	Enabled Size: 2048 MB (Single-bank Connection)
	Error Status: OK

Handle 0x0027, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x0024
	Memory Array Mapped Address Handle: 0x002D
	Partition Row Position: 1

Handle 0x0028, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x0023
	Error Information Handle: 0x0029
	Total Width: 64 bits
	Data Width: 8 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK0
	Type: <OUT OF SPEC>
	Type Detail: Synchronous
	Speed: 1066 MHz (0.9 ns)
	Manufacturer: Samsung
	Serial Number: 8429C56F
	Asset Tag: Unknown
	Part Number: M471B5673FH0-CF8  

Handle 0x0029, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x002A, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM1
	Bank Connections: None
	Current Speed: Unknown
	Type: Unknown DIMM
	Installed Size: 2048 MB (Single-bank Connection)
	Enabled Size: 2048 MB (Single-bank Connection)
	Error Status: OK

Handle 0x002B, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00080000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 2 GB
	Physical Device Handle: 0x0028
	Memory Array Mapped Address Handle: 0x002D
	Partition Row Position: 1

Handle 0x002C, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x002D, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Physical Array Handle: 0x0023
	Partition Width: 0

Handle 0x002E, DMI type 5, 20 bytes
Memory Controller Information
	Error Detecting Method: None
	Error Correcting Capabilities:
		Unknown
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 4096 MB
	Maximum Total Memory Size: 8192 MB
	Supported Speeds:
		Other
	Supported Memory Types:
		Other
	Memory Module Voltage: Unknown
	Associated Memory Slots: 2
		0x0026
		0x002A
	Enabled Error Correcting Capabilities:
		None

Handle 0x002F, DMI type 127, 4 bytes
End Of Table

```

Thank you for any piece of advice to find out what's going on.

---

