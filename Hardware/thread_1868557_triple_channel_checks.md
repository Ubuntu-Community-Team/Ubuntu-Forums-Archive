---
title: "triple channel checks"
date: 2011-10-24
forum: Hardware
---

### Post by andreammilazzo on 2011-10-24
Dear all,
first of all thank for the great work.
I have to perform some memory tests in an intel i7-960 processor but I m not able to find any command that give me an answer of the type numbers of channel that the Integrated memory contol use.
I only know that there are 6 memory bank of 2GB.
I also try to guess but decode-dimms (after the activation of the eeprom module) gave me 0 module found.
I tried lshw and dmidecode(as su) but the output is as follow:
 the output of sudo lshw is:

    description: Desktop Computer
    product: System Product Name
    vendor: System manufacturer
    version: System Version
    serial: System Serial Number
    width: 64 bits
    capabilities: smbios-2.5 dmi-2.5 vsyscall64 vsyscall32
    configuration: boot=normal chassis=desktop uuid=00AD001E-8C00-00DB-4682-20CF3014C90C
  *-core
       description: Motherboard
       product: P6T DELUXE V2
       vendor: ASUSTeK Computer INC.
       physical id: 0
       version: Rev 1.xx
       serial: 105976480000475
       slot: To Be Filled By O.E.M.
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: 0901 (02/24/2010)
          size: 64KiB
          capacity: 1984KiB
          capabilities: isa pci pnp apm upgrade shadowing escd cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM) i7 CPU         960  @ 3.20GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: Intel(R) Core(TM) i7 CPU 960 @ 3.20GHz
          serial: To Be Filled By O.E.M.
          slot: LGA1366
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 133MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts rep_good xtopology nonstop_tsc aperfmperf pni dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 popcnt lahf_lm ida tpr_shadow vnmi flexpriority ept vpid cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KiB
             capacity: 256KiB
             capabilities: internal write-through instruction
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: internal write-through unified
        *-cache:2
             description: L3 cache
             physical id: 7
             slot: L3-Cache
             size: 8MiB
             capacity: 8MiB
             capabilities: internal write-back unified
     *-memory
          description: System Memory
          physical id: 40
          slot: System board or motherboard
          size: 12GiB
        *-bank:0
             description: DIMM 1066 MHz (0.9 ns)
             product: ModulePartNumber00
             vendor: Manufacturer00
             physical id: 0
             serial: SerNum00
             slot: DIMM0
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:1
             description: DIMM 1066 MHz (0.9 ns)
             product: ModulePartNumber01
             vendor: Manufacturer01
             physical id: 1
             serial: SerNum01
             slot: DIMM1
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:2
             description: DIMM 1066 MHz (0.9 ns)
             product: ModulePartNumber02
             vendor: Manufacturer02
             physical id: 2
             serial: SerNum02
             slot: DIMM2
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:3
             description: DIMM 1066 MHz (0.9 ns)
             product: ModulePartNumber03
             vendor: Manufacturer03
             physical id: 3
             serial: SerNum03
             slot: DIMM3
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:4
             description: DIMM 1066 MHz (0.9 ns)
             product: ModulePartNumber04
             vendor: Manufacturer04
             physical id: 4
             serial: SerNum04
             slot: DIMM4
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
        *-bank:5
             description: DIMM 1066 MHz (0.9 ns)
             product: ModulePartNumber05
             vendor: Manufacturer05
             physical id: 5
             serial: SerNum05
             slot: DIMM5
             size: 2GiB
             width: 64 bits
             clock: 1066MHz (0.9ns)
(it was removed the useful infos) 

the output of  sudo dmidecode is:


# dmidecode 2.9
SMBIOS 2.5 present.
81 structures occupying 3016 bytes.
Table at 0x000F0700.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: 0901   
	Release Date: 02/24/2010
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 2048 kB
	Characteristics:
		ISA is supported
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
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
	BIOS Revision: 8.15

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: System manufacturer
	Product Name: System Product Name
	Version: System Version
	Serial Number: System Serial Number
	UUID: 00AD001E-8C00-00DB-4682-20CF3014C90C
	Wake-up Type: Power Switch
	SKU Number: To Be Filled By O.E.M.
	Family: To Be Filled By O.E.M.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: ASUSTeK Computer INC.
	Product Name: P6T DELUXE V2
	Version: Rev 1.xx
	Serial Number: 105976480000475
	Asset Tag: To Be Filled By O.E.M.
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To Be Filled By O.E.M.
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0003, DMI type 3, 21 bytes
Chassis Information
	Manufacturer: Chassis Manufacture
	Type: Desktop
	Lock: Not Present
	Version: Chassis Version
	Serial Number: Chassis Serial Number
	Asset Tag: Asset-1234567890
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000001
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0

Handle 0x0004, DMI type 4, 40 bytes
Processor Information
	Socket Designation: LGA1366
	Type: Central Processor
	Family: <OUT OF SPEC>
	Manufacturer: Intel            
	ID: A5 06 01 00 FF FB EB BF
	Version: Intel(R) Core(TM) i7 CPU 960 @ 3.20GHz              
	Voltage: 1.2 V
	External Clock: 133 MHz
	Max Speed: 3200 MHz
	Current Speed: 3200 MHz
	Status: Populated, Enabled
	Upgrade: Other
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: 0x0007
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Part Number: To Be Filled By O.E.M.
	Core Count: 4
	Core Enabled: 4
	Thread Count: 8
	Characteristics:
		64-bit capable

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1-Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 256 KB
	Maximum Size: 256 KB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Parity
	System Type: Instruction
	Associativity: 4-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2-Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 1024 KB
	Maximum Size: 1024 KB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 8-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L3-Cache
	Configuration: Enabled, Not Socketed, Level 3
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 8192 KB
	Maximum Size: 8192 KB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 16-way Set-associative

Handle 0x0008, DMI type 5, 28 bytes
Memory Controller Information
	Error Detecting Method: 64-bit ECC
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 4096 MB
	Maximum Total Memory Size: 24576 MB
	Supported Speeds:
		70 ns
		60 ns
	Supported Memory Types:
		DIMM
		SDRAM
	Memory Module Voltage: 3.3 V
	Associated Memory Slots: 6
		0x0009
		0x000A
		0x000B
		0x000C
		0x000D
		0x000E
	Enabled Error Correcting Capabilities:
		None

Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM0
	Bank Connections: 1
	Current Speed: 1 ns
	Type: DIMM
	Installed Size: 2048 MB (Single-bank Connection)
	Enabled Size: 2048 MB (Single-bank Connection)
	Error Status: OK

Handle 0x000A, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM1
	Bank Connections: 2
	Current Speed: 1 ns
	Type: DIMM
	Installed Size: 2048 MB (Single-bank Connection)
	Enabled Size: 2048 MB (Single-bank Connection)
	Error Status: OK

Handle 0x000B, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM2
	Bank Connections: 3
	Current Speed: 1 ns
	Type: DIMM
	Installed Size: 2048 MB (Single-bank Connection)
	Enabled Size: 2048 MB (Single-bank Connection)
	Error Status: OK

Handle 0x000C, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM3
	Bank Connections: 4
	Current Speed: 1 ns
	Type: DIMM
	Installed Size: 2048 MB (Single-bank Connection)
	Enabled Size: 2048 MB (Single-bank Connection)
	Error Status: OK

Handle 0x000D, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM4
	Bank Connections: 5
	Current Speed: 1 ns
	Type: DIMM
	Installed Size: 2048 MB (Single-bank Connection)
	Enabled Size: 2048 MB (Single-bank Connection)
	Error Status: OK

Handle 0x000E, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM5
	Bank Connections: 6
	Current Speed: 1 ns
	Type: DIMM
	Installed Size: 2048 MB (Single-bank Connection)
	Enabled Size: 2048 MB (Single-bank Connection)
	Error Status: OK

other stuff ....


Handle 0x0040, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: Multi-bit ECC
	Maximum Capacity: 24 GB
	Error Information Handle: Not Provided
	Number Of Devices: 6

Handle 0x0041, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Array Handle: 0x0040
	Partition Width: 0

Handle 0x0042, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0040
	Error Information Handle: Not Provided
	Total Width: 72 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK0
	Type: Other
	Type Detail: Other
	Speed: 1066 MHz (0.9 ns)
	Manufacturer: Manufacturer00
	Serial Number: SerNum00
	Asset Tag: AssetTagNum0
	Part Number: ModulePartNumber00

Handle 0x0043, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Device Handle: 0x0042
	Memory Array Mapped Address Handle: 0x0041
	Partition Row Position: 1
	Interleave Position: Unknown
	Interleaved Data Depth: 2

Handle 0x0044, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0040
	Error Information Handle: Not Provided
	Total Width: 72 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK1
	Type: Other
	Type Detail: Other
	Speed: 1066 MHz (0.9 ns)
	Manufacturer: Manufacturer01
	Serial Number: SerNum01
	Asset Tag: AssetTagNum1
	Part Number: ModulePartNumber01

Handle 0x0045, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Device Handle: 0x0044
	Memory Array Mapped Address Handle: 0x0041
	Partition Row Position: 1
	Interleave Position: Unknown
	Interleaved Data Depth: 2

Handle 0x0046, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0040
	Error Information Handle: Not Provided
	Total Width: 72 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM2
	Bank Locator: BANK2
	Type: Other
	Type Detail: Other
	Speed: 1066 MHz (0.9 ns)
	Manufacturer: Manufacturer02
	Serial Number: SerNum02
	Asset Tag: AssetTagNum2
	Part Number: ModulePartNumber02

Handle 0x0047, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Device Handle: 0x0046
	Memory Array Mapped Address Handle: 0x0041
	Partition Row Position: 1
	Interleave Position: Unknown
	Interleaved Data Depth: 2

Handle 0x0048, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0040
	Error Information Handle: Not Provided
	Total Width: 72 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM3
	Bank Locator: BANK3
	Type: Other
	Type Detail: Other
	Speed: 1066 MHz (0.9 ns)
	Manufacturer: Manufacturer03
	Serial Number: SerNum03
	Asset Tag: AssetTagNum3
	Part Number: ModulePartNumber03

Handle 0x0049, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Device Handle: 0x0048
	Memory Array Mapped Address Handle: 0x0041
	Partition Row Position: 1
	Interleave Position: Unknown
	Interleaved Data Depth: 2

Handle 0x004A, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0040
	Error Information Handle: Not Provided
	Total Width: 72 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM4
	Bank Locator: BANK4
	Type: Other
	Type Detail: Other
	Speed: 1066 MHz (0.9 ns)
	Manufacturer: Manufacturer04
	Serial Number: SerNum04
	Asset Tag: AssetTagNum4
	Part Number: ModulePartNumber04

Handle 0x004B, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Device Handle: 0x004A
	Memory Array Mapped Address Handle: 0x0041
	Partition Row Position: 1
	Interleave Position: Unknown
	Interleaved Data Depth: 2

Handle 0x004C, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0040
	Error Information Handle: Not Provided
	Total Width: 72 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM5
	Bank Locator: BANK5
	Type: Other
	Type Detail: Other
	Speed: 1066 MHz (0.9 ns)
	Manufacturer: Manufacturer05
	Serial Number: SerNum05
	Asset Tag: AssetTagNum5
	Part Number: ModulePartNumber05

Handle 0x004D, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000000003FF
	Range Size: 1 kB
	Physical Device Handle: 0x004C
	Memory Array Mapped Address Handle: 0x0041
	Partition Row Position: 1
	Interleave Position: Unknown
	Interleaved Data Depth: 2

---

