---
title: "ThinkPad with Lucid won't hibernate or suspend"
date: 2010-07-30
forum: Hardware
---

### Post by matthewglen on 2010-07-30
[INDENT]This is a very long-winded post. If you want to offer help without reading all of it, the problem in its simplest terms is that hibernate/suspend results in a partial shutdown, leaving the screen, fan, and possibly other hardware running, and yielding the computer entirely unresponsive.[/INDENT]

I've done some searching about this and tried solutions from a couple different threads, but it sounds like it's fairly hit and miss, and I've only managed to miss.

The problem is that when I try to hibernate or suspend my computer, it starts the process but doesn't finish. To be more specific, the screen goes black, but remains on, and the sleep light begins flashing more quickly than I think it should (I'd guess about two or three flashes per second). Then it just stays at that position. If I close the laptop lid, the screen stays on and the light stays flashing. The keyboard is entirely unresponsive (I've tried Enter, Esc, Ctrl+Alt+Delete, Alt+F2, and various other keys and combinations), as is the ThinkVantage button (although I've never really found anything that it does except make it easier to enter BIOS on startup). Pressing the power button yields no response, and I have to hold it and kill the computer. Startup then takes very slightly longer than when I do a clean shutdown, but there aren't any problems (aside from any programs I was running telling me they ended unexpectedly when I open them again).

Everything past this point might be more information than is needed, but I figured it'd be easiest to supply as much possibly relevant info as I can. 

I have tried using both the Power Manager suspend and hibernate functions, as well as hibernate-ram from the command line. The same thing always happens.

I use my laptop a lot, but I find it a huge hassle to close and reopen all of my programs every time I use it, and I certainly don't want to leave it running.

Like I said, I've done some searching, both here and on the web in general, and have found several posts about this general problem, but haven't found a viable solution.

I would be grateful for direct advice or links to relevant threads.

I would rate my understanding of Linux as beginner to moderate, so I might not understand overly-technical jargon, however if it's explained in somewhat simpler terms, I'm very able to navigate the OS.

--

Thinkpad T61 14.1" w/: Intel Core 2 Duo T9300 @ 2.5Ghz, integrated NVidia Quadro NVS 140M graphics, PC2-5300 2DIMM memory, and A-Data 500 series SSD

I have run Ubuntu on this computer for two years (originaly 7.04 Feisty), and hibernate/suspend used to work. I can't remember exactly when the problem started, but I'm tempted to say it was with the install of 9.10 Karmic. I installed 10.04 shortly after its release, and have since replaced the HDD with an SSD and done a clean install of Ubuntu 10.04.1 LTS.

```
$ uname -a
Linux Greg 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:20:59 UTC 2010 x86_64 GNU/Linux
```

```
$ sudo dmidecode -q
BIOS Information
	Vendor: LENOVO
	Version: 7LETB7WW (2.17 )
	Release Date: 04/25/2008
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 4096 kB
	Characteristics:
		PCI is supported
		PC Card (PCMCIA) is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		ACPI is supported
		USB legacy is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 2.23
	Firmware Revision: 1.8

System Information
	Manufacturer: LENOVO
	Product Name: 7662CTO
	Version: ThinkPad T61

Base Board Information
	Manufacturer: LENOVO
	Product Name: 7662CTO

Processor Information
	Socket Designation: None
	Type: Central Processor
	Family: Other
	Manufacturer: GenuineIntel
	ID: 76 06 01 00 FF FB EB BF
	Version: Intel(R) Core(TM)2 Duo CPU     T9300  @ 2.50GHz
	Voltage: 1.2 V
	External Clock: 200 MHz
	Max Speed: 2500 MHz
	Current Speed: 2500 MHz
	Status: Populated, Enabled
	Upgrade: None
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

Memory Controller Information
	Error Detecting Method: None
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: One-way Interleave
	Maximum Memory Module Size: 4096 MB
	Maximum Total Memory Size: 8192 MB
	Supported Speeds:
		Other
	Supported Memory Types:
		DIMM
		SDRAM
	Memory Module Voltage: 2.9 V
	Associated Memory Slots: 2
		0x0008
		0x0009
	Enabled Error Correcting Capabilities:
		Unknown

Memory Module Information
	Socket Designation: DIMM Slot 1
	Bank Connections: 0 1
	Current Speed: 155 ns
	Type: DIMM SDRAM
	Installed Size: 1024 MB (Double-bank Connection)
	Enabled Size: 1024 MB (Double-bank Connection)
	Error Status: OK

Memory Module Information
	Socket Designation: DIMM Slot 2
	Bank Connections: 2 3
	Current Speed: 155 ns
	Type: DIMM SDRAM
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK

Cache Information
	Socket Designation: Internal L1 Cache
	Configuration: Enabled, Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 64 KB
	Maximum Size: 64 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Instruction
	Associativity: 8-way Set-associative

Cache Information
	Socket Designation: Internal L1 Cache
	Configuration: Enabled, Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 64 KB
	Maximum Size: 64 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Data
	Associativity: 8-way Set-associative

Cache Information
	Socket Designation: Internal L2 Cache
	Configuration: Enabled, Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 6144 KB
	Maximum Size: 6144 KB
	Supported SRAM Types:
		Burst
	Installed SRAM Type: Burst
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 8-way Set-associative

System Slot Information
	Designation: Media Card Slot 1
	Type: Other
	Current Usage: Available
	Length: Other
	Characteristics:
		Hot-plug devices are supported

On Board Device Information
	Type: Other
	Status: Enabled
	Description: IBM Embedded Security hardware

OEM Strings
	String 1: IBM ThinkPad Embedded Controller -[7KHT24WW-1.08    ]-

BIOS Language Information
	Installable Languages: 1
		enUS
	Currently Installed Language: enUS

System Event Log
	Area Length: 0 bytes
	Header Start Offset: 0x0000
	Header Length: 16 bytes
	Data Start Offset: 0x0010
	Access Method: General-purpose non-volatile data functions
	Access Address: 0x0000
	Status: Valid, Not Full
	Change Token: 0x000000B7
	Header Format: Type 1
	Supported Log Type Descriptors: 1
	Descriptor 1: POST error
	Data Format 1: POST results bitmap

Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Number Of Devices: 2

Memory Device
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 1024 MB
	Form Factor: SODIMM
	Set: None
	Locator: DIMM 1
	Bank Locator: Bank 0/1
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

Memory Device
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: SODIMM
	Set: None
	Locator: DIMM 2
	Bank Locator: Bank 2/3
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified

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
	Ending Address: 0x000BFFFFFFF
	Range Size: 3 GB
	Partition Width: 0

Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 1 GB
	Partition Row Position: 1

Memory Device Mapped Address
	Starting Address: 0x00040000000
	Ending Address: 0x000BFFFFFFF
	Range Size: 2 GB
	Partition Row Position: 1

```
(I removed a few things from this that seemed entirely superfluous)

If there's any info I can give that could be of more help, let me know. Your help is greatly appreciated.

---

