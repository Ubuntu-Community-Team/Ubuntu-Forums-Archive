---
title: "Strange Hardware Issue"
date: 2012-12-31
forum: Hardware
---

### Post by jonhall on 2012-12-31
Hello,

We have been experiencing a strange problem with one of our Ubuntu boxes running version 12.10 with kernel 3.5.0-21 (64 bit). Every so often it completely freezes up and the display starts flashing colored blocks all over the screen (see attached image). This seems to occur randomly, and the only option to recover is a hard reboot (I can't even SSH into the system when this occurs). I believe it is a hardware issue, since it also occurred when running memtest from a bootable CD, so it's not specific to the Ubuntu install.

Any suggestions for troubleshooting this problem? This is a custom-built PC. The output of ```
dmidecode -q
``` is below. Please let me know if any other information would be helpful.

Thanks!

```

BIOS Information
	Vendor: American Megatrends Inc.
	Version: V1.7
	Release Date: 03/07/2011
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 8192 kB
	Characteristics:
		PCI is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 kB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		ACPI is supported
		USB legacy is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
		UEFI is supported
	BIOS Revision: 4.6

System Information
	Manufacturer: MSI
	Product Name: MS-7678
	Version: 1.0
	Serial Number: To be filled by O.E.M.
	UUID: 00000000-0000-0000-0000-6C626D45DD02
	Wake-up Type: Power Switch
	SKU Number: To be filled by O.E.M.
	Family: To be filled by O.E.M.

Base Board Information
	Manufacturer: MSI
	Product Name: H67MA-E45 (MS-7678)
	Version: 1.0
	Serial Number: To be filled by O.E.M.
	Asset Tag: To be filled by O.E.M.
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: To be filled by O.E.M.
	Type: Motherboard

Chassis Information
	Manufacturer: MSI
	Type: Desktop
	Lock: Not Present
	Version: 1.0
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0
	SKU Number: To be filled by O.E.M.

Cache Information
	Socket Designation: Not Specified
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Varies With Memory Address
	Location: Internal
	Installed Size: 256 kB
	Maximum Size: 256 kB
	Supported SRAM Types:
		Unknown
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Other
	Associativity: 8-way Set-associative

Cache Information
	Socket Designation: Not Specified
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Varies With Memory Address
	Location: Internal
	Installed Size: 1024 kB
	Maximum Size: 1024 kB
	Supported SRAM Types:
		Unknown
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unified
	Associativity: 8-way Set-associative

Cache Information
	Socket Designation: Not Specified
	Configuration: Enabled, Not Socketed, Level 3
	Operational Mode: Varies With Memory Address
	Location: Internal
	Installed Size: 6144 kB
	Maximum Size: 6144 kB
	Supported SRAM Types:
		Unknown
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unified
	Associativity: Other

Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: PS2Mouse
	External Connector Type: PS/2
	Port Type: Mouse Port

Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: Keyboard
	External Connector Type: PS/2
	Port Type: Keyboard Port

Port Connector Information
	Internal Reference Designator: J2A2A
	Internal Connector Type: None
	External Reference Designator: COM A
	External Connector Type: DB-9 male
	Port Type: Serial Port 16550A Compatible

Port Connector Information
	Internal Reference Designator: J3A1
	Internal Connector Type: None
	External Reference Designator: USB1
	External Connector Type: Access Bus (USB)
	Port Type: USB

Port Connector Information
	Internal Reference Designator: J3A1
	Internal Connector Type: None
	External Reference Designator: USB2
	External Connector Type: Access Bus (USB)
	Port Type: USB

Port Connector Information
	Internal Reference Designator: J5A1
	Internal Connector Type: None
	External Reference Designator: LAN
	External Connector Type: RJ-45
	Port Type: Network Port

Port Connector Information
	Internal Reference Designator: J9A1 - TPM HDR
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Port Connector Information
	Internal Reference Designator: J9C1 - PCIE DOCKING CONN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Port Connector Information
	Internal Reference Designator: J2B3 - CPU FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Port Connector Information
	Internal Reference Designator: J9E2 - MDC INTPSR
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Port Connector Information
	Internal Reference Designator: J9E4 - MDC INTPSR
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Port Connector Information
	Internal Reference Designator: J9E1 - SCAN MATRIX
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Port Connector Information
	Internal Reference Designator: J9G1 - LPC SIDE BAND
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Port Connector Information
	Internal Reference Designator: J8F1 - UNIFIED
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Port Connector Information
	Internal Reference Designator: J1G6 - AC JACK
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Port Connector Information
	Internal Reference Designator: J1G7 - BATT B
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Port Connector Information
	Internal Reference Designator: J1H1 - BATT A
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Port Connector Information
	Internal Reference Designator: J7H2 - SATA PWR
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Port Connector Information
	Internal Reference Designator: J7H1 - SATA PORT2
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Port Connector Information
	Internal Reference Designator: J7J3 - SATA PORT1
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Port Connector Information
	Internal Reference Designator: J8J1 - SATA PORT0
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Port Connector Information
	Internal Reference Designator: J4J1 - ATX PWR
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

System Slot Information
	Designation: J6B2
	Type: x16 PCI Express
	Current Usage: Available
	Length: Long
	ID: 0
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported
	Bus Address: 0000:ff:01.0

System Slot Information
	Designation: J6B1
	Type: x1 PCI Express
	Current Usage: Available
	Length: Short
	ID: 1
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported
	Bus Address: 0000:01:1c.0

System Slot Information
	Designation: J6D1
	Type: x1 PCI Express
	Current Usage: Available
	Length: Short
	ID: 2
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported
	Bus Address: 0000:ff:1c.1

System Slot Information
	Designation: J7B1
	Type: x1 PCI Express
	Current Usage: Available
	Length: Short
	ID: 3
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported
	Bus Address: 0000:ff:1c.2

OEM Strings
	String 1: To Be Filled By O.E.M.

System Configuration Options
	Option 1: To Be Filled By O.E.M.

Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 32 GB
	Number Of Devices: 4

32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Partition Width: 1

Memory Device
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: A1_DIMM0
	Bank Locator: A1_BANK0
	Type: DDR3
	Type Detail: Synchronous
	Speed: 1333 MHz
	Manufacturer: Undefined       
	Serial Number: 00000000  
	Asset Tag: A1_AssetTagNum0
	Part Number: 1333EL Series     
	Rank: 1
	Configured Clock Speed: Unknown

32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Partition Row Position: 1

Memory Device
	Total Width: 64 bits
	Data Width: 64 bits
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: A1_DIMM1
	Bank Locator: A1_BANK1
	Type: Unknown
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: A1_Manufacturer1
	Serial Number: A1_SerNum1
	Asset Tag: A1_AssetTagNum1
	Part Number: Array1_PartNumber1
	Rank: Unknown
	Configured Clock Speed: Unknown

32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Memory Device
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: A1_DIMM2
	Bank Locator: A1_BANK2
	Type: DDR3
	Type Detail: Synchronous
	Speed: 1333 MHz
	Manufacturer: Undefined       
	Serial Number: 00000000  
	Asset Tag: A1_AssetTagNum2
	Part Number: 1333EL Series     
	Rank: 1
	Configured Clock Speed: 58785 MHz

32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Memory Device Mapped Address
	Starting Address: 0x00080000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 2 GB
	Partition Row Position: 1

Memory Device
	Total Width: 64 bits
	Data Width: 64 bits
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: A1_DIMM3
	Bank Locator: A1_BANK3
	Type: Unknown
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: A1_Manufacturer3
	Serial Number: A1_SerNum3
	Asset Tag: A1_AssetTagNum3
	Part Number: Array1_PartNumber3
	Rank: Unknown
	Configured Clock Speed: 66 MHz

32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

System Boot Information
	Status: No errors detected

Management Device
	Description: LM78-1
	Type: LM78
	Address: 0x00000000
	Address Type: I/O Port

Voltage Probe
	Description: LM78A
	Location: <OUT OF SPEC>
	Status: <OUT OF SPEC>
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000
	Nominal Value: Unknown

Management Device Threshold Data
	Lower Non-critical Threshold: 1
	Upper Non-critical Threshold: 2
	Lower Critical Threshold: 3
	Upper Critical Threshold: 4
	Lower Non-recoverable Threshold: 5
	Upper Non-recoverable Threshold: 6

Management Device Component
	Description: To Be Filled By O.E.M.

Temperature Probe
	Description: LM78A
	Location: <OUT OF SPEC>
	Status: <OUT OF SPEC>
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000
	Nominal Value: Unknown

Management Device Threshold Data
	Lower Non-critical Threshold: 1
	Upper Non-critical Threshold: 2
	Lower Critical Threshold: 3
	Upper Critical Threshold: 4
	Lower Non-recoverable Threshold: 5
	Upper Non-recoverable Threshold: 6

Management Device Component
	Description: To Be Filled By O.E.M.

Cooling Device
	Type: <OUT OF SPEC>
	Status: <OUT OF SPEC>
	Cooling Unit Group: 1
	OEM-specific Information: 0x00000000
	Nominal Speed: Unknown Or Non-rotating
	Description: Cooling Dev 1

Management Device Threshold Data
	Lower Non-critical Threshold: 1
	Upper Non-critical Threshold: 2
	Lower Critical Threshold: 3
	Upper Critical Threshold: 4
	Lower Non-recoverable Threshold: 5
	Upper Non-recoverable Threshold: 6

Management Device Component
	Description: To Be Filled By O.E.M.

Cooling Device
	Type: <OUT OF SPEC>
	Status: <OUT OF SPEC>
	Cooling Unit Group: 1
	OEM-specific Information: 0x00000000
	Nominal Speed: Unknown Or Non-rotating
	Description: Not Specified

Management Device Threshold Data
	Lower Non-critical Threshold: 1
	Upper Non-critical Threshold: 2
	Lower Critical Threshold: 3
	Upper Critical Threshold: 4
	Lower Non-recoverable Threshold: 5
	Upper Non-recoverable Threshold: 6

Management Device Component
	Description: To Be Filled By O.E.M.

Electrical Current Probe
	Description: ABC
	Location: <OUT OF SPEC>
	Status: <OUT OF SPEC>
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000
	Nominal Value: Unknown

Management Device Threshold Data

Management Device Component
	Description: To Be Filled By O.E.M.

System Power Supply
	Power Unit Group: 1
	Location: To Be Filled By O.E.M.
	Name: To Be Filled By O.E.M.
	Manufacturer: To Be Filled By O.E.M.
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Model Part Number: To Be Filled By O.E.M.
	Revision: To Be Filled By O.E.M.
	Max Power Capacity: Unknown
	Status: Not Present
	Type: <OUT OF SPEC>
	Input Voltage Range Switching: <OUT OF SPEC>
	Plugged: Yes
	Hot Replaceable: No

Management Device
	Description: 2
	Type: LM78
	Address: 0x00000000
	Address Type: I/O Port

Voltage Probe
	Description: LM78B
	Location: <OUT OF SPEC>
	Status: <OUT OF SPEC>
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000
	Nominal Value: Unknown

Management Device Threshold Data
	Lower Non-critical Threshold: 7
	Upper Non-critical Threshold: 8
	Lower Critical Threshold: 8
	Upper Critical Threshold: 10
	Lower Non-recoverable Threshold: 11
	Upper Non-recoverable Threshold: 12

Management Device Component
	Description: To Be Filled By O.E.M.

Voltage Probe
	Description: LM78B
	Location: <OUT OF SPEC>
	Status: <OUT OF SPEC>
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000
	Nominal Value: Unknown

Management Device Threshold Data
	Lower Non-critical Threshold: 13
	Upper Non-critical Threshold: 14
	Lower Critical Threshold: 15
	Upper Critical Threshold: 16
	Lower Non-recoverable Threshold: 17
	Upper Non-recoverable Threshold: 18

Management Device Component
	Description: To Be Filled By O.E.M.

Temperature Probe
	Description: LM78B
	Location: <OUT OF SPEC>
	Status: <OUT OF SPEC>
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000
	Nominal Value: Unknown

Management Device Threshold Data
	Lower Non-critical Threshold: 1
	Upper Non-critical Threshold: 2
	Lower Critical Threshold: 3
	Upper Critical Threshold: 4
	Lower Non-recoverable Threshold: 5
	Upper Non-recoverable Threshold: 6

Management Device Component
	Description: To Be Filled By O.E.M.

Cooling Device
	Type: <OUT OF SPEC>
	Status: <OUT OF SPEC>
	Cooling Unit Group: 1
	OEM-specific Information: 0x00000000
	Nominal Speed: Unknown Or Non-rotating
	Description: Cooling Dev 2

Management Device Threshold Data
	Lower Non-critical Threshold: 1
	Upper Non-critical Threshold: 2
	Lower Critical Threshold: 3
	Upper Critical Threshold: 4
	Lower Non-recoverable Threshold: 5
	Upper Non-recoverable Threshold: 6

Management Device Component
	Description: To Be Filled By O.E.M.

Temperature Probe
	Description: LM78B
	Location: <OUT OF SPEC>
	Status: <OUT OF SPEC>
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000
	Nominal Value: Unknown

Management Device Threshold Data
	Lower Non-critical Threshold: 1
	Upper Non-critical Threshold: 2
	Lower Critical Threshold: 3
	Upper Critical Threshold: 4
	Lower Non-recoverable Threshold: 5
	Upper Non-recoverable Threshold: 6

Management Device Component
	Description: To Be Filled By O.E.M.

Cooling Device
	Type: <OUT OF SPEC>
	Status: <OUT OF SPEC>
	Cooling Unit Group: 1
	OEM-specific Information: 0x00000000
	Nominal Speed: Unknown Or Non-rotating
	Description: Cooling Dev 2

Management Device Threshold Data
	Lower Non-critical Threshold: 1
	Upper Non-critical Threshold: 2
	Lower Critical Threshold: 3
	Upper Critical Threshold: 4
	Lower Non-recoverable Threshold: 5
	Upper Non-recoverable Threshold: 6

Management Device Component
	Description: To Be Filled By O.E.M.

Electrical Current Probe
	Description: DEF
	Location: <OUT OF SPEC>
	Status: <OUT OF SPEC>
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000
	Nominal Value: Unknown

Management Device Threshold Data

Management Device Component
	Description: To Be Filled By O.E.M.

Electrical Current Probe
	Description: GHI
	Location: <OUT OF SPEC>
	Status: <OUT OF SPEC>
	Maximum Value: Unknown
	Minimum Value: Unknown
	Resolution: Unknown
	Tolerance: Unknown
	Accuracy: Unknown
	OEM-specific Information: 0x00000000
	Nominal Value: Unknown

Management Device Threshold Data

Management Device Component
	Description: To Be Filled By O.E.M.

System Power Supply
	Power Unit Group: 1
	Location: To Be Filled By O.E.M.
	Name: To Be Filled By O.E.M.
	Manufacturer: To Be Filled By O.E.M.
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Model Part Number: To Be Filled By O.E.M.
	Revision: To Be Filled By O.E.M.
	Max Power Capacity: Unknown
	Status: Not Present
	Type: <OUT OF SPEC>
	Input Voltage Range Switching: <OUT OF SPEC>
	Plugged: Yes
	Hot Replaceable: No

Processor Information
	Socket Designation: SOCKET 0
	Type: Central Processor
	Family: Core i5
	Manufacturer: Intel
	ID: A7 06 02 00 FF FB EB BF
	Signature: Type 0, Family 6, Model 42, Stepping 7
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
	Version: Intel(R) Core(TM) i5-2300 CPU @ 2.80GHz
	Voltage: 0.0 V
	External Clock: 100 MHz
	Max Speed: 3800 MHz
	Current Speed: 1600 MHz
	Status: Populated, Enabled
	Upgrade: Socket BGA1155
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified
	Core Count: 4
	Core Enabled: 4
	Thread Count: 4
	Characteristics:
		64-bit capable

BIOS Language Information
	Language Description Format: Long
	Installable Languages: 15
		en|US|iso8859-1
		<BAD INDEX>
		<BAD INDEX>
		<BAD INDEX>
		<BAD INDEX>
		<BAD INDEX>
		<BAD INDEX>
		<BAD INDEX>
		<BAD INDEX>
		<BAD INDEX>
		<BAD INDEX>
		<BAD INDEX>
		<BAD INDEX>
		<BAD INDEX>
		<BAD INDEX>
	Currently Installed Language: en|US|iso8859-1

```

---

### Post by matt_symes on 2012-12-31
Hi

What do your logs say around the time it crashes ?

Kind regards

---

### Post by ahallubuntu on 2012-12-31
What's the history of this box?  Was it fine for a while then suddenly started this behavior?  Or has it always been this way?

I'd try to remove as much as you can and still POST and run Memtest.  So, unplug all drives, USB devices (except keyboard) and other add-in cards that you can and see if you can run Memtest successfully.

Does Memtest do the same thing (screen-wise)?  Or does it just have other issues?

I couldn't get from your posted info whether this has a discrete video card or whether you are using integrated video - but if you have a separate card, you might try re-seating it.  Or, if there's an option to remove it and use onboard video for testing, try that.  But the issue may have nothing to do with video.

Some possibilities that come to mind:
- bad or incompatible RAM
- CPU overheating (fan not working or clogged with dust dirt; heat sink not seated properly)
- power supply failing or underpowered for the hardware
- motherboard failing (look for possible blown caps, though this appears not to be an ancient motherboard)

---

### Post by tgalati4 on 2013-01-01
Strip everything out of the machine, minimum RAM, perhaps another graphics card and test it.  Run memtest for 30 complete passes.  Then try running Ubuntu for a few days in this minimum condition.  Test your power supply with a voltmeter while it's running.

If it passes, then add components one at a time, running a few days to see any change in behavior.  It could be a defective motherboard.  They are assembled with toothpaste and hot glue these days.

---

### Post by jonhall on 2013-01-01
Thanks for the tips/pointers! The PC is about 1.5 years old. I don't remember noticing this problem right after it was built, but it has been happening for quite a while now. I checked the system log and there is nothing unusual around the time that it crashed. I also thought of CPU overheating and have kept an eye on temps, but I haven't noticed anything out of the ordinary. 

Memtest does run successfully (usually); I just had the same screen issue once when running memtest, which led me to the conclusion that it's probably a hardware issue rather than a software/OS problem. The system is fairly bare-bones; there isn't a lot connected to it, no expansion cards, and it's using integrated video.

I haven't tested the PSU; perhaps I should look there. Otherwise I would think it's probably the motherboard, but I'm not sure how to know for sure. It may still be under warranty, but since this is a fairly random problem I'm not sure how to prove that it's defective.

---

### Post by tgalati4 on 2013-01-01
Put your finger on the integrated graphics chip/heatsink.  If you can't keep your finger on it (because it is too hot), then that might be your problem.  Add a small fan to the heatsink, or put in another video card so that the integrated video is turned off.

---

### Post by jonhall on 2013-01-01
Hmmm... right now it's warm, but not hot. I'll have to try that when it crashes next to see what it feels like then. Thanks for the suggestion!

---

### Post by ahallubuntu on 2013-01-01
> **jonhall said:**
> Memtest does run successfully (usually);

What do you mean "usually?"  Have you tried other RAM besides what's in there now?  It should ALWAYS run successfully unless you have some other reason for it.

You could have bad RAM or RAM that's not compatible with that motherboard.

---

### Post by jonhall on 2013-01-01
What I meant is that memtest doesn't fail or report any memory errors. However, the computer has crashed while running memtest, in the same way that it has when running Ubuntu.

---

### Post by tgalati4 on 2013-01-01
It is common for graphics chips and IO-bridge chips to delaminate from the motherboard.  They are soldered to the motherboard with ~700 balls of tiny solder, known as ball grid array (BGA).  With lead-free solder of newer boards, these joints fail on chips that get hot.  Pressure on the chip can make contact and improve uptime, but repair is difficult with high failure rate.  Of course it could be a corroded copper trace on the motherboard.  The fact that the machine locks up during memtest is a good indicator that the motherboard is suspect.  But you can't rule out the power supply either.  All it takes is one capacitor to start shorting when hot and you have power dropouts.

---

### Post by Linuxisfast on 2013-01-01
Most likely its your vga cable or video card going bad, mine did the same before it packed off.

---

