---
title: "Turning a desktop into a server"
date: 2008-11-19
forum: Hardware
---

### Post by rozilla on 2008-11-19
I've got a few desktops that I want to use as servers. 

Here is what dmidecode tells me on the specs:

> BIOS Information
	Vendor: American Megatrends Inc.
	Version: 5.22
	Release Date: 12/12/2007
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 512 kB
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
		Function key-initiated network boot is supported
		Targeted content distribution is supported
	BIOS Revision: 5.22

System Information
	Manufacturer: HP-Pavilion
	Product Name: GS209AA-ABV dx2290MT
	Version:  
	Serial Number: CNX8040G41
	UUID: C4AB1A3A-C0C9-DC11-92AB-78ED0731C45C
	Wake-up Type: Power Switch
	SKU Number: GS209AA#ABV
	Family: 103C_53316J

Base Board Information
	Manufacturer: ECS                                                            
	Product Name: Livermore8
	Version: 1.0
	Serial Number:                                      
	Asset Tag:                                      
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis:                                      
	Type: Motherboard

Chassis Information
	Manufacturer: Hewlett-Packard                                                 
	Type: Desktop
	Lock: Not Present
	Version:                                      
	Serial Number:                                      
	Asset Tag:                                      
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0

Processor Information
	Socket Designation: CPU 1
	Type: Central Processor
	Family: Other
	Manufacturer: Intel            
	ID: FD 06 00 00 FF FB EB BF
	Version: Intel(R) Pentium(R) Dual  CPU  E2160  @ 1.80GHz     
	Voltage: 1.3 V
	External Clock: 200 MHz
	Max Speed: 1800 MHz
	Current Speed: 1800 MHz
	Status: Populated, Enabled
	Upgrade: Other
	Serial Number:                       
	Asset Tag:                       
	Part Number:                       

Cache Information
	Socket Designation: L1-Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 64 KB
	Maximum Size: 64 KB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Parity
	System Type: Data
	Associativity: 8-way Set-associative

Cache Information
	Socket Designation: L2-Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 1024 KB
	Maximum Size: 1024 KB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Instruction
	Associativity: 8-way Set-associative

Memory Controller Information
	Error Detecting Method: 64-bit ECC
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
	Memory Module Voltage: 3.3 V
	Associated Memory Slots: 2
		0x0008
		0x0009
	Enabled Error Correcting Capabilities:
		None

Memory Module Information
	Socket Designation: DIMM0
	Bank Connections: 0 1
	Current Speed: Unknown
	Type: DIMM SDRAM
	Installed Size: 512 MB (Single-bank Connection)
	Enabled Size: 512 MB (Single-bank Connection)
	Error Status: OK

Memory Module Information
	Socket Designation: DIMM1
	Bank Connections: 4 5
	Current Speed: Unknown
	Type: DIMM SDRAM
	Installed Size: 512 MB (Single-bank Connection)
	Enabled Size: 512 MB (Single-bank Connection)
	Error Status: OK

OEM Strings
	String 1: bid=44APfdBNR1,44APfdBNR1;ACPwrFail=Off;Chan=Retail;CPUFan=On;DV
	String 2: DRW;LegacyFloppy=No;TVout=PAL;PCBRAND=Pavilion;OS=LX;.rm;##
	String 3:  
	String 4:  
	String 5:  
	String 6:  
	String 7:  
	String 8:  
	String 9:  
	String 10:  
	String 11:  
	String 12:  
	String 13:  
	String 14:  
	String 15:  
	String 16:  
	String 17:  
	String 18:  
	String 19:  
	String 20:  
	String 21:  
	String 22:  
	String 23:  
	String 24:  
	String 25:  
	String 26:  
	String 27:  
	String 28:  
	String 29:  
	String 30:  
	String 31:  
	String 32:  

BIOS Language Information
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1

System Event Log
	Area Length: 4 bytes
	Header Start Offset: 0x0000
	Header Length: 2 bytes
	Data Start Offset: 0x0002
	Access Method: Indexed I/O, one 16-bit index port, one 8-bit data port
	Access Address: Index 0x046A, Data 0x046C
	Status: Invalid, Not Full
	Change Token: 0x00000000
	Header Format: No Header
	Supported Log Type Descriptors: 6
	Descriptor 1: End of log
	Data Format 1: OEM-specific
	Descriptor 2: End of log
	Data Format 2: OEM-specific
	Descriptor 3: End of log
	Data Format 3: OEM-specific
	Descriptor 4: End of log
	Data Format 4: OEM-specific
	Descriptor 5: End of log
	Data Format 5: OEM-specific
	Descriptor 6: End of log
	Data Format 6: OEM-specific

Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Number Of Devices: 2

Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 1 GB
	Partition Width: 0

Memory Device
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK0
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: 7F7F7F7F7F510000                          
	Serial Number: Ser0
	Asset Tag: Num0
	Part Number: 64T64000HU3SB     

Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0001FFFFFFF
	Range Size: 512 MB
	Partition Row Position: 1
	Interleaved Data Depth: 1

Memory Device
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK1
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz (1.5 ns)
	Manufacturer: 7F7F7F7FCB000000                          
	Serial Number: Ser1
	Asset Tag: Num1
	Part Number:  DQPE1908         

Memory Device Mapped Address
	Starting Address: 0x00020000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 512 MB
	Partition Row Position: 1
	Interleaved Data Depth: 1

System Boot Information
	Status: No errors detected



What I want it for one desktop to be a firewall server, that includes DHCP, NS, LDAP. And another desktop would be a fileserver, with NFS and SystemImager in the mix. What would you say are the minimum recommended specs regarding disk space, memory, and processor speed?

---

### Post by rigol2000 on 2008-11-19
I don't have the information you need to your specific requirements, but FYI: I ran a wiki from Ubuntu 8.04.1 with an HTML server on a Dell desktop running a Pentium III 700MHz with 256MB of ram.  It ran pretty smoothly but a little slow at times.  Granted, my DSL upstream speed was the main culprit. 

My *very green* opinion is that your systems meet the minimums.  

My 2 cents  :) Hope it helps.

---

### Post by cariboo on 2008-11-19
If you have the desktop version of Ubuntu installed already, open a Applications-->Accessories-->Terminal and type:

```
sudo tasksel
```

This will pop up a menu with the different severs that are installable.

If you are planning on using the server version of Ubuntu, the server selections are part of the installation. Be aware that the server version does not install a gui.

Jim

---

### Post by rozilla on 2008-11-22
> **rigol2000 said:**
> I don't have the information you need to your specific requirements, but FYI: I ran a wiki from Ubuntu 8.04.1 with an HTML server on a Dell desktop running a Pentium III 700MHz with 256MB of ram.  It ran pretty smoothly but a little slow at times.  Granted, my DSL upstream speed was the main culprit. 

My *very green* opinion is that your systems meet the minimums.  

My 2 cents  :) Hope it helps.

How many users did you have on that Dell? Any idea? I'm expecting about 100 users during the day, off an on, depending on peak times and whatnot. This number should increase by 50-70 in the coming months.


> **cariboo907 said:**
> If you have the desktop version of Ubuntu installed already, open a Applications-->Accessories-->Terminal and type:

```
sudo tasksel
```

This will pop up a menu with the different severs that are installable.

If you are planning on using the server version of Ubuntu, the server selections are part of the installation. Be aware that the server version does not install a gui.

Jim

No GUI? Damn. Our systems guy is going to kill himself! ;-)

---

### Post by rigol2000 on 2008-11-22
> **rozilla said:**
> How many users did you have on that Dell? Any idea? I'm expecting about 100 users during the day, off an on, depending on peak times and whatnot. This number should increase by 50-70 in the coming months.

Not that many at all.  Maybe 10.

---

### Post by sdennie on 2008-11-22
As long as you aren't talking about extreme loads (which, it doesn't sound like you are), if a machine is powerful enough to run the desktop software reasonably, it should handle moderate server load without breaking a sweat.  The CPU you mention is quite capable but, 512M of RAM could become a problem at some point.

---

