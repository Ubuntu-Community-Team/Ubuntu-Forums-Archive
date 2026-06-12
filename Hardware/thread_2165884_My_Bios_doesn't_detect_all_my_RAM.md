---
title: "My Bios doesn't detect all my RAM"
date: 2013-08-06
forum: Hardware
---

### Post by joan_carles2 on 2013-08-06
First of all I use Ubuntu. Today I bought a DIM of 2 GB.

I had another DIM already installed. So totally should be 4 GB but my bios only detects 3.2

I've checked my motherboard. its next model and seems to support 4GB

My BIOS is: Ambios V02.59 American megatrends 12/17/2007

I've checked different option with my BIOS And I haven't succed. Ubuntu detects the same RAM as my Bios. Windows says that I have 4 GB but I can only use 3.2.

My  VGA video card only should take 64MB of RAM.

I've also tried to put 1 DIM. Checke dthat detected 2 GB. Then I tried separetely the other DIM and also worked well. I also tried different combination in the slots...

I don't know what else to try. Anyone can give some advice?

---

### Post by newbie-user on 2013-08-06
Older 32-bit systems won't be able to use anything above 3.5GB of ram. Try using a 64-bit OS. BIOS or chipset may also have the same limitation, since it's older.

---

### Post by joan_carles2 on 2013-08-06
my ubuntu is amd64. Should should detect 4GB. It's not a problem of new or old

The problem I think is with the bios that only detect 3GB. MAybe is assigning 1GB to some hardware  but i don't know which one.

---

### Post by sanderj on 2013-08-06
get the script on [http://www.appelboor.com/dump/check-my-memory.py](http://www.appelboor.com/dump/check-my-memory.py) , and run it as root ("sudo python check-my-memory.py") ... it will tell all the details you need.

---

### Post by newbie-user on 2013-08-06
> **joan_carles2 said:**
> my ubuntu is amd64. Should should detect 4GB. It's not a problem of new or old

The problem I think is with the bios that only detect 3GB. MAybe is assigning 1GB to some hardware  but i don't know which one.

Then it's probably the BIOS that is causing it. I have some ASUS P5L-MX boards at work that do that same thing. The BIOS only reports 3.5GB while I have 4GB installed.

---

### Post by JDorfler on 2013-08-06
Silly question.  Are the two sticks the exact same sticks from the exact same manufacturer?  Even then it isn't a guarentee.  The G. Skill website recommends you just not add sticks, but make sure they came from the same pack.

---

### Post by Mk32 on 2013-08-06
If the CPU supports PAE, then a PAE compatible kernel will let you use more than the 3.2/3.5GB limitation of traditional 32 bit CPUs.

---

### Post by codemaniac on 2013-08-07
*Thread moved to **Hardware**.*

---

### Post by joan_carles2 on 2013-08-07
Tonight I will check if both DIM are identical. For sure my CPU supports PAE and my system is amd64. It's not only the OS that detects only 3.13GB. It's the OS and the BIOS.  My motherboard it's P4M900T-M2 (V2.0)

You can check the specification here:

[http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?DetailID=822&MenuID=16](http://www.ecs.com.tw/ECSWebSite/Product/Product_Detail.aspx?DetailID=822&MenuID=16)

You will see that the motherboard supports 4 GB

I will also try to run the script in py. Thks everyone to help me on this issue. I will report the results of all your suggestions.

---

### Post by 1clue on 2013-08-07
If your bios only detects 3.13 then that's where the problem is IMO.  Go get a bios upgrade.

Edit:
That is, it's either bios or incompatible sticks.  If you're using amd64 it's not in Linux.  I've got 12g and it all shows up, and I use most of it.

---

### Post by joan_carles2 on 2013-08-07
1clue. How I can find out if my version of BIOS can only detect 3.13? Before upgrading the BIOS I want to be sure that this is the problem. Upgrade the BIOS it's serious and If I mess it up.... can be a huge problem.

As I told you at the beginning the BIOS that I have is next:

[COLOR=#000000]My BIOS is: Ambios V02.59 American megatrends 12/17/2007


[/COLOR]

---

### Post by 1clue on 2013-08-07
It's easy.  You have 4g of physical RAM.  If they're both the same thing, the board should pick up all of it.  I know some boards can be fussy about that, but I've had sticks of different sizes and different manufacturers on one box and everything was recognized.

If your RAM is all the same and your BIOS only sees 3.13g then your BIOS isn't recognizing it.  Go look up your motherboard model, check for a new bios and look at the logs for everything after your BIOS.  If it says something about recognizing more memory, then that's probably the problem.

This is like a chain.  The first point where you see something wrong, that's where the problem is.  It goes hardware, bios, operating system.  If it's a hardware problem then nothing you can do in the bios can fix it.  Likewise if your bios doesn't recognize your memory then there's nothing you can do in the operating system to get it.

I bios upgrade is sort of a big deal, but if you're careful it's not really a problem.  Read the instructions from the manufacturer.  Download the file and make sure the checksum matches.

---

### Post by Yellow Pasque on 2013-08-07
Output of dmidecode might be helpful:
```
sudo apt-get install dmidecode
sudo dmidecode
```

> If your RAM is all the same and your BIOS only sees 3.13g then your BIOS isn't recognizing it.
More likely, the BIOS is "recognizing" the RAM, but reserving it for hardware addressing.

---

### Post by 1clue on 2013-08-07
Almost a gigabyte of hardware addressing?  I doubt that.

---

### Post by joan_carles2 on 2013-08-07
Well. Let's inform you about the obtained results. In the next link you will find a picture of my DIM. I'm not an expert but I would say that they should be compatible. If not please let me know it

[http://img560.imageshack.us/img560/7172/dt5h.jpg](http://img560.imageshack.us/img560/7172/dt5h.jpg)

I also really hesitate that 1GB is addressed to somewhere. Only 64MB should be addressed to the VGA output.

The output of next command is:

joan@ubuntu:~$ sudo dmidecode
# dmidecode 2.12
SMBIOS 2.5 present.
47 structures occupying 1637 bytes.
Table at 0x000FC7C0.


Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: 080014 
	Release Date: 12/17/2007
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
		3.5"/720 kB floppy services are supported (int 13h)
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
	BIOS Revision: 8.14


Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: DataLogic
	Product Name: P4M900T-M2
	Version: 2.0
	Serial Number: 00000000
	UUID: 00020003-0004-0005-0006-000700080009
	Wake-up Type: Power Switch
	SKU Number: To Be Filled By O.E.M.
	Family: To Be Filled By O.E.M.


Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: ECS
	Product Name: P4M900T-M2
	Version: 2.0
	Serial Number: 00000000
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
	Manufacturer: ECS
	Type: Desktop
	Lock: Not Present
	Version: 2.0
	Serial Number: 00000000
	Asset Tag: 0123ABC
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0


Handle 0x0004, DMI type 4, 40 bytes
Processor Information
	Socket Designation: CPU 1
	Type: Central Processor
	Family: Unknown
	Manufacturer: Intel            
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
		FXSR (FXSAVE and FXSTOR instructions supported)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		SS (Self-snoop)
		HTT (Multi-threading)
		TM (Thermal monitor supported)
		PBE (Pending break enabled)
	Version: Intel(R) Pentium(R) Dual  CPU  E2180  @ 2.00GHz     
	Voltage: 1.3 V
	External Clock: 200 MHz
	Max Speed: 2000 MHz
	Current Speed: 2000 MHz
	Status: Populated, Enabled
	Upgrade: Socket 478
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: 0x0007
	Serial Number: To Be Filled By O.E.M.
	Asset Tag: To Be Filled By O.E.M.
	Part Number: To Be Filled By O.E.M.
	Characteristics: None


Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1-Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 64 kB
	Maximum Size: 64 kB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Parity
	System Type: Data
	Associativity: 8-way Set-associative


Handle 0x0006, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2-Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 1024 kB
	Maximum Size: 1024 kB
	Supported SRAM Types:
		Other
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Instruction
	Associativity: 8-way Set-associative


Handle 0x0007, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L3-Cache
	Configuration: Disabled, Not Socketed, Level 3
	Operational Mode: Unknown
	Location: Internal
	Installed Size: 0 kB
	Maximum Size: 0 kB
	Supported SRAM Types:
		Unknown
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown


Handle 0x0008, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM0
	Bank Connections: 1 0
	Current Speed: Unknown
	Type: SDRAM
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK


Handle 0x0009, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: DIMM1
	Bank Connections: 3 2
	Current Speed: Unknown
	Type: SDRAM
	Installed Size: 2048 MB (Double-bank Connection)
	Enabled Size: 2048 MB (Double-bank Connection)
	Error Status: OK


Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: PS2Mouse
	External Connector Type: PS/2
	Port Type: Mouse Port


Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1A1
	Internal Connector Type: None
	External Reference Designator: Keyboard
	External Connector Type: PS/2
	Port Type: Keyboard Port


Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A2
	Internal Connector Type: None
	External Reference Designator: USB1
	External Connector Type: Access Bus (USB)
	Port Type: USB


Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A2
	Internal Connector Type: None
	External Reference Designator: USB2
	External Connector Type: Access Bus (USB)
	Port Type: USB


Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J4A1
	Internal Connector Type: None
	External Reference Designator: LPT 1
	External Connector Type: DB-25 male
	Port Type: Parallel Port ECP/EPP


Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2A1
	Internal Connector Type: None
	External Reference Designator: COM A
	External Connector Type: DB-9 male
	Port Type: Serial Port 16550A Compatible


Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6A1
	Internal Connector Type: None
	External Reference Designator: Audio Mic In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port


Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6A1
	Internal Connector Type: None
	External Reference Designator: Audio Line In
	External Connector Type: Mini Jack (headphones)
	Port Type: Audio Port


Handle 0x0012, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6B1 - AUX IN
	Internal Connector Type: On Board Sound Input From CD-ROM
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Audio Port


Handle 0x0013, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6B2 - CDIN
	Internal Connector Type: On Board Sound Input From CD-ROM
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Audio Port


Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6J2 - PRI IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other


Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6J1 - SEC IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other


Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J4J1 - FLOPPY
	Internal Connector Type: On Board Floppy
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other


Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9H1 - FRONT PNL
	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other


Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J1B1 - CHASSIS REAR FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other


Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2F1 - CPU FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other


Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8B4 - FRONT FAN
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other


Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9G2 - FNT USB
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other


Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J6C3 - FP AUD
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other


Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9G1 - CONFIG
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other


Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J8C1 - SCSI LED
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other


Handle 0x001F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9J2 - INTRUDER
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other


Handle 0x0020, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J9G4 - ITP
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other


Handle 0x0021, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: J2H1 - MAIN POWER
	Internal Connector Type: Other
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other


Handle 0x0022, DMI type 9, 13 bytes
System Slot Information
	Designation: AGP
	Type: 32-bit AGP 4x
	Current Usage: Available
	Length: Short
	ID: 0
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported


Handle 0x0023, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI1
	Type: 32-bit PCI
	Current Usage: Available
	Length: Short
	ID: 1
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported


Handle 0x0024, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description:   To Be Filled By O.E.M.


Handle 0x0025, DMI type 13, 22 bytes
BIOS Language Information
	Language Description Format: Abbreviated
	Installable Languages: 1
		en|US|iso8859-1
	Currently Installed Language: en|US|iso8859-1


Handle 0x0026, DMI type 15, 35 bytes
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


Handle 0x0027, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 4 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2


Handle 0x0028, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x00000000BFF
	Range Size: 3 kB
	Physical Array Handle: 0x0027
	Partition Width: 1


Handle 0x0029, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0027
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM0
	Bank Locator: BANK0
	Type: DDR2
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Manufacturer0
	Serial Number: SerNum0
	Asset Tag: AssetTagNum0
	Part Number: PartNum0


Handle 0x002A, DMI type 126, 19 bytes
Inactive


Handle 0x002B, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0027
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: None
	Locator: DIMM1
	Bank Locator: BANK1
	Type: DDR2
	Type Detail: Synchronous
	Speed: Unknown
	Manufacturer: Manufacturer1
	Serial Number: SerNum1
	Asset Tag: AssetTagNum1
	Part Number: PartNum1


Handle 0x002C, DMI type 126, 19 bytes
Inactive


Handle 0x002D, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected


Handle 0x002E, DMI type 127, 4 bytes
End Of Table

---

### Post by joan_carles2 on 2013-08-07
This is the result of the phyton script

joan@ubuntu:~$ sudo python check-my-memory.py
[sudo] password for joan: 
check-my-memory.py - version: SJ 2013-02-22
OK, you're root
ANALYSIS:
Total of physical memory modules found 4096 MB in 2 memory module(s)
BIOS offers 3261 MB as usable
Memory seen by OS 3208 MB
BIOS version 12/17/2007
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit


SUMMARY:
Memory difference between DIMM hardware and BIOS offering 835 MB
Memory difference between BIOS offering and memory seen by OS 53 MB
Memory difference between DIMM hardware and memory seen by OS 888 MB


ADVICE:
Your BIOS is not offering all of your physical memory. Try to update your BIOS, and/or enable 'memory hole remapping / hoisting' in your BIOS to get more usable memory


Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...
       description: System Memory
       size: 4GiB
          description: DIMM DDR2 Synchronous
          size: 2GiB
          description: DIMM DDR2 Synchronous
          size: 2GiB


Finished


According to all the information that I gave I do believe that next step is update the BIOS. I'm scared But I will try to do it. If you see something wrong with the provided information please let me know it.

---

### Post by joan_carles2 on 2013-08-07
I've updated the BIOS and problem is not solved. Now I'm running the last Bios version that the manufacturer of the motherboard has in his website. And the problem is still there.

---

### Post by sanderj on 2013-08-08
> **joan_carles2 said:**
> This is the result of the phyton script

joan@ubuntu:~$ sudo python check-my-memory.py
[sudo] password for joan: 
check-my-memory.py - version: SJ 2013-02-22
OK, you're root
ANALYSIS:
Total of physical memory modules found 4096 MB in 2 memory module(s)
BIOS offers 3261 MB as usable
Memory seen by OS 3208 MB
BIOS version 12/17/2007
CPU is PAE enabled
CPU is x86_64 64-bit enabled
OS is x86_64 64-bit


SUMMARY:
Memory difference between DIMM hardware and BIOS offering 835 MB
Memory difference between BIOS offering and memory seen by OS 53 MB
Memory difference between DIMM hardware and memory seen by OS 888 MB


ADVICE:
Your BIOS is not offering all of your physical memory. Try to update your BIOS, and/or enable 'memory hole remapping / hoisting' in your BIOS to get more usable memory


Finally: show more detailed memory info from lshw. This can take up to 30 seconds ...
       description: System Memory
       size: 4GiB
          description: DIMM DDR2 Synchronous
          size: 2GiB
          description: DIMM DDR2 Synchronous
          size: 2GiB


Finished


According to all the information that I gave I do believe that next step is update the BIOS. I'm scared But I will try to do it. If you see something wrong with the provided information please let me know it.

Good that you ran the script. As a BIOS update does not solve it, can you go into the BIOS setup and try to find 'memory hole remapping / hoisting'?

---

### Post by joan_carles2 on 2013-08-08
Hi sanderj

I can't find this option in my BIOS "[COLOR=#000000]memory hole remapping / hoisting"

I just can't find it. In the next link you can find pics of my BIOS setup. The pictures are before updating the BIOS.... However after updating there are no new options... So the pictures should be useful in order that someane can advice me about the setup option that I should modify:

[/COLOR][http://img24.imageshack.us/img24/8820/wdq0.jpg](http://img24.imageshack.us/img24/8820/wdq0.jpg)
[http://img833.imageshack.us/img833/5245/up4w.jpg](http://img833.imageshack.us/img833/5245/up4w.jpg)
[http://img542.imageshack.us/img542/4118/rqd5.jpg](http://img542.imageshack.us/img542/4118/rqd5.jpg)
[http://img837.imageshack.us/img837/2953/z52j.jpg](http://img837.imageshack.us/img837/2953/z52j.jpg)
[http://img10.imageshack.us/img10/5470/5ill.jpg](http://img10.imageshack.us/img10/5470/5ill.jpg)
[http://img845.imageshack.us/img845/8965/efrb.jpg](http://img845.imageshack.us/img845/8965/efrb.jpg)
[http://img5.imageshack.us/img5/7715/san0.jpg](http://img5.imageshack.us/img5/7715/san0.jpg)
[http://img841.imageshack.us/img841/8837/pnkj.jpg](http://img841.imageshack.us/img841/8837/pnkj.jpg)
[http://img850.imageshack.us/img850/7988/h4qf.jpg](http://img850.imageshack.us/img850/7988/h4qf.jpg)
[http://img580.imageshack.us/img580/883/c9l7.jpg](http://img580.imageshack.us/img580/883/c9l7.jpg)

---

### Post by Yellow Pasque on 2013-08-08
I don't see any settings in your BIOS that would change it. I really think it's a limitation of the VIA P4m900 chipset, as googling around shows other people with that chipset complaining of the same thing. Anyway, it's not a big deal unless you use a lot of RAM.

---

### Post by joan_carles2 on 2013-08-08
I've sent an email to ECS website in order to know if it's a problem of the motherboard or not. For sure if this is a Generalized BIOS problem or a motherboard limitation they will let me know it.

If they reply me I will inform you.

---

### Post by joan_carles2 on 2013-08-25
Hi to everyone. This is the reply that The manufacturer of the Motherboard give. Do you think that the reply is reasonable? (In my opinion they are kidding. I repeat thousands of times to them that the problem is that the BIOS doesn't detect the 4GB and they focus on the software that I use.) Seems that each time reply me a different person. They really have a bad costumer service. Here is the reply that ECS ([http://www.ecs.com.tw]("http://www.ecs.com.tw/")) gave  me. I want to know your opinion

Dear Sir

We can't visit the link. [http://img560.imageshack.us/img560/7172/dt5h.jpg](http://img560.imageshack.us/img560/7172/dt5h.jpg)


I check the information of this problem, the P4M8XX/P4M9XX chipset can't fully support 4G memory.
Excerpt:
If a computer has 4 gigabytes (GB) of random-access memory (RAM) installed, the system memory that is reported in the System Information dialog box in Windows XP is less than you expect. For example, the System Information dialog box may report 3,120 megabytes (MB) of system memory on a computer that has 4 GB of memory installed (4,096 MB).
If a computer has many installed devices, the available memory may be reduced to 3 GB or less. However, the maximum memory available in 32-bit versions of Windows Vista is typically 3.12 GB.
For example, before you upgrade to Windows XP SP2, the System Properties dialog box may report approximately 3.87 GB of RAM. The System Information tool may report that the total physical memory is approximately 3,540.00 megabytes (MB). After you upgrade to Windows XP SP2, the System Properties dialog box may report approximately 3.12 GB of RAM, and the System Information tool may report that the total physical memory is approximately 2,770.00 MB.


Best regards,
Technical Support Dept.

---

### Post by Yellow Pasque on 2013-08-25
Yeah, that equals my experience with tech support from motherboard companies. Enjoy this comic: [http://xkcd.com/806/](http://xkcd.com/806/)

---

### Post by sanderj on 2013-08-25
You got a reply from ECS, the mobo / computer company? Wow, impressive.

Now back to your memory: your BIOS says "BIOS version 12/17/2007". That means your hardware is older, so 2007 or older. It's now 2013. That's 6 years or more. In 2007 (or before) we were still in the Windows Vista era and 4GB was very much memory. There were all kinds of tricks and problems supporting it.

So, my point of view is that you can't blame the tech company now for 2007 hardware. You get 3.2 GB RAM effectively, and I can imagine that's annoying, but I would say try to live with that, or consider buying newer hardware.

Just my point of view.

---

### Post by joan_carles2 on 2013-08-25
haha

I'm not anoyed. In fact I'm not a gamer. For the use that I give to the computer in my opinion I still have computer for years. You also must notice that in linux there are extremly light distros. So help you to enlarge the life the computer. I have a ****** notebook with a celeron processor of 900 MHz and 1 GB of RAM. The computer is still usable Xubuntu. It's faster than you imagine. I still could use another lighter distro to this computer with openbox for example.

I really give up with the costumer service of this company. Trust that I talked to them many times. I explained the problem and they always reply the same. It is so easy. They just have to tell me it's possible or it's not possible. If it's not possible then let me know the reason....   Seems that for them this is impossible.  They just know that if you install windows xp 32 bits you can't use the 4 GB.... (well at least they know something)

In my opinion the bios doesn't support memory remapping.... So this is the reason because I can't use the 4 GB. But well I will never know it for sure because the manufacturer doesn't know it either.

Well Thks for your support and also thanks for the comic. I will keep on fighting with ECS people. I think that I deserve a better reply. I don't mind if the computer can detect 4GB or not... The problem is the explanations that they give...

Bye

---

### Post by 1clue on 2013-08-25
What they're saying is reasonable.  If there's a chip on the board that can't support more than 4g, then there's a good chance you'd run into some issues as though you had a 32-bit OS even if you're using 64-bit.

Seriously, before you spend a lot of time on this board, go look at fry's or newegg and see how much new boards or even fully assembled desktops go for now.  An atom is likely to keep up with what was typical on a desktop 6 years ago.  You'll be amazed how cheap they are, and you're pretty much certain to get 2 cores or more.  Not saying you have to go swap out if you don't want, but if you're trying for 4g I think it's probably because you ran out of memory, so this is not a futile exercise.

---

### Post by joan_carles2 on 2013-08-25
I don't complain about my hardware. So no need to look for a new hard.

I just complain that when you read the specifications of the motherboard they say that supports 4 GB and this is not true. Now frankly speaking I Don't mind if 3.2 or 4.

---

### Post by sergi2 on 2013-08-25
Hello joan_carles2!

Can you pass me the ECS e-mail?? want to send another mail too. I have the same problem with this motherboard (I also have the same two kingston memories that you have), but with the difference that any of the programs that I run detected the 4gb of memory, but only 3gb! I updated bios and checked everything but still nothing....

PS: are you català by the way??

---

### Post by joan_carles2 on 2013-08-26
Hi Sergi

I'm catalan. I think that you won't solve anything because this motherboard just don't support 4 GB. And the problem in my opinon is the BIOS (the last version it's from the end of 2008). Anyway please try it. You will see that they will get nonsense replies.

There is no email. You must go to their website.

Then click on the button Support
Then you must fill the support form. They will ask you some information of your PC and they will give you an email.
Then once the form is sent they will give you a number. With this number and you email you could check the replies that they give you.

If you get something please let me know it.

---

