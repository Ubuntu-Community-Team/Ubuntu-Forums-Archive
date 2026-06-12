---
title: "What kind of RAM (graphics card?) can I put in this desktop?"
date: 2010-01-31
forum: Hardware
---

### Post by Zorgoth on 2010-01-31
I have a desktop with 1GB DDR.  I want to upgrade it to 2GB DDR.  What I want to know is how do I know if a RAM chip I buy is compatible with my computer and what kind of performance is reasonable to look for)  I am also replacing the graphics card obviously, probably with a GeForce 9400; I assume I am right that I can do this?.

Here is the output of sudo dmidecode:

```


ubuntu@ubuntu:~$ sudo dmidecode
# dmidecode 2.9
SMBIOS 2.3 present.
33 structures occupying 984 bytes.
Table at 0x000F0000.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Phoenix Technologies, LTD
	Version: 6.00 PG
	Release Date: 10/20/2004
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 512 kB
	Characteristics:
		PCI is supported
		PNP is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/360 KB floppy services are supported (int 13h)
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
		AGP is supported
		LS-120 boot is supported
		ATAPI Zip drive boot is supported
		BIOS boot specification is supported

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer:  
	Product Name:  
	Version:  
	Serial Number:  
	UUID: 00000000-0000-0000-0000-00508DD3312B
	Wake-up Type: Power Switch
	SKU Number:  
	Family:  

Handle 0x0002, DMI type 2, 8 bytes
Base Board Information
	Manufacturer: http://www.abit.com.tw/
	Product Name: KV80/KV81/KV82(VIA K8M800-8237)
	Version: 1.x  
	Serial Number:  

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
	Manufacturer:  
	Type: Desktop
	Lock: Not Present
	Version:  
	Serial Number:  
	Asset Tag:  
	Boot-up State: Unknown
	Power Supply State: Unknown
	Thermal State: Unknown
	Security Status: Unknown
	OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
	Socket Designation: Socket 754
	Type: Central Processor
	Family: Athlon 64
	Manufacturer: AMD
	ID: C0 0F 00 00 FF FB 8B 07
	Signature: Family 15, Model 12, Stepping 0
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
		MMX (MMX technology supported)
		FXSR (Fast floating-point save and restore)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
	Version: AMD Athlon(tm) 64 Processor 3000+
	Voltage: 1.5 V
	External Clock: 200 MHz
	Max Speed: 3000 MHz
	Current Speed: 2000 MHz
	Status: Populated, Enabled
	Upgrade: Socket 754
	L1 Cache Handle: 0x0008
	L2 Cache Handle: 0x0009
	L3 Cache Handle: Not Provided
	Serial Number:  
	Asset Tag:  
	Part Number:  

Handle 0x0005, DMI type 5, 20 bytes
Memory Controller Information
	Error Detecting Method: 64-bit ECC
	Error Correcting Capabilities:
		None
	Supported Interleave: One-way Interleave
	Current Interleave: Four-way Interleave
	Maximum Memory Module Size: 4096 MB
	Maximum Total Memory Size: 8192 MB
	Supported Speeds:
		70 ns
		60 ns
		50 ns
	Supported Memory Types:
		Standard
		DIMM
	Memory Module Voltage: 2.9 V
	Associated Memory Slots: 2
		0x0006
		0x0007
	Enabled Error Correcting Capabilities: None

Handle 0x0006, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A0
	Bank Connections: 0 1
	Current Speed: 6 ns
	Type: Unknown EDO
	Installed Size: 512 MB (Double-bank Connection)
	Enabled Size: 512 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0007, DMI type 6, 12 bytes
Memory Module Information
	Socket Designation: A1
	Bank Connections: 2 3
	Current Speed: 6 ns
	Type: Unknown EDO
	Installed Size: 512 MB (Double-bank Connection)
	Enabled Size: 512 MB (Double-bank Connection)
	Error Status: OK

Handle 0x0008, DMI type 7, 19 bytes
Cache Information
	Socket Designation: Internal Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 128 KB
	Maximum Size: 128 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x0009, DMI type 7, 19 bytes
Cache Information
	Socket Designation: External Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 512 KB
	Maximum Size: 512 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x000A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: PRIMARY IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x000B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: SECONDARY IDE
	Internal Connector Type: On Board IDE
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: Other

Handle 0x000C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: FDD
	Internal Connector Type: On Board Floppy
	External Reference Designator: Not Specified
	External Connector Type: None
	Port Type: 8251 FIFO Compatible

Handle 0x000D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: COM1
	Internal Connector Type: 9 Pin Dual Inline (pin 10 cut)
	External Reference Designator:  
	External Connector Type: DB-9 male
	Port Type: Serial Port 16450 Compatible

Handle 0x000E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: LPT1
	Internal Connector Type: DB-25 female
	External Reference Designator:  
	External Connector Type: DB-25 female
	Port Type: Parallel Port ECP/EPP

Handle 0x000F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Keyboard
	Internal Connector Type: PS/2
	External Reference Designator:  
	External Connector Type: PS/2
	Port Type: Keyboard Port

Handle 0x0010, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: PS/2 Mouse
	Internal Connector Type: PS/2
	External Reference Designator:  
	External Connector Type: PS/2
	Port Type: Mouse Port

Handle 0x0011, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: Not Specified
	Internal Connector Type: None
	External Reference Designator: USB0
	External Connector Type: Other
	Port Type: USB

Handle 0x0012, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI0
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 1
	Characteristics:
		5.0 V is provided
		PME signal is supported

Handle 0x0013, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI1
	Type: 32-bit PCI
	Current Usage: Available
	Length: Long
	ID: 2
	Characteristics:
		5.0 V is provided
		PME signal is supported

Handle 0x0014, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI2
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 3
	Characteristics:
		5.0 V is provided
		PME signal is supported

Handle 0x0015, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI3
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 4
	Characteristics:
		5.0 V is provided
		PME signal is supported

Handle 0x0016, DMI type 9, 13 bytes
System Slot Information
	Designation: PCI4
	Type: 32-bit PCI
	Current Usage: In Use
	Length: Long
	ID: 0
	Characteristics:
		5.0 V is provided
		PME signal is supported

Handle 0x0017, DMI type 9, 13 bytes
System Slot Information
	Designation: AGP
	Type: 32-bit AGP
	Current Usage: In Use
	Length: Long
	ID: 8
	Characteristics:
		5.0 V is provided

Handle 0x0018, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 3
		n|US|iso8859-1
		n|US|iso8859-1
		r|CA|iso8859-1
	Currently Installed Language: n|US|iso8859-1

Handle 0x0019, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 8 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x001A, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0019
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: A0
	Bank Locator: Bank0/1
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: None
	Serial Number: None
	Asset Tag: None
	Part Number: None

Handle 0x001B, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x0019
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: DIMM
	Set: None
	Locator: A1
	Bank Locator: Bank2/3
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: None
	Serial Number: None
	Asset Tag: None
	Part Number: None

Handle 0x001C, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 1 GB
	Physical Array Handle: 0x0019
	Partition Width: 0

Handle 0x001D, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0001FFFFFFF
	Range Size: 512 MB
	Physical Device Handle: 0x001A
	Memory Array Mapped Address Handle: 0x001C
	Partition Row Position: 1

Handle 0x001E, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00020000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 512 MB
	Physical Device Handle: 0x001B
	Memory Array Mapped Address Handle: 0x001C
	Partition Row Position: 1

Handle 0x001F, DMI type 32, 11 bytes
System Boot Information
	Status: No errors detected

Handle 0x0020, DMI type 127, 4 bytes
End Of Table


```

Thanks!

---

### Post by Yellow Pasque on 2010-01-31
You have a Socket 754 board with DDR memory and an AGP slot. Just get a pair of DDR400 sticks. New graphics cards use PCI-E, so you're probably not going to be able to upgrade the graphics.

---

### Post by Mze on 2010-01-31
Going with this [info]("http://www.dealtime.com/xPF-Abit-KV-80-Mainboard-for-S754K8M800-SATA-ATA-GbLAN-ATX-SOUND-VGA-RAID") about your motherboard, you will be able to use 1 gig RAM modules in each slot. 

Your maximum RAM supported is 2 gig.

The motherboard supports PC2100 (266 Mhz), PC2700 (333 Mhz) and PC3200.

Go with PC3200 (400 Mhz) as the older RAM will most probably cost you more. You do have to make sure both modules are the same, can't mix match frequencies.

Your board supports AGP 8x, so make sure the graphics card you're getting is an AGP one.

---

### Post by Zorgoth on 2010-01-31
OK so I am thinking about these upgrades:

[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=320402898516&rvr_id=&crlp=1_263602_263622&UA=L*F%3F&GUID=850c79951260a0aad2c191d1ff0c65ac&itemid=320402898516&ff4=263602_263622](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=320402898516&rvr_id=&crlp=1_263602_263622&UA=L*F%3F&GUID=850c79951260a0aad2c191d1ff0c65ac&itemid=320402898516&ff4=263602_263622)

for memory (2GB PC3200) and

[http://www.compuvest.com/Search.jsp?Search=256-A8-N536-BX&advsite=froogle&dtm=20100129&sku=331004029-02](http://www.compuvest.com/Search.jsp?Search=256-A8-N536-BX&advsite=froogle&dtm=20100129&sku=331004029-02)

for graphics (GeForce 7600 AGP) - there were better deals on ATI cards but my Dad wants to run Second Life and they have a bad reputation for that.  If anyone in the know has comments about the 7600 AGP 256MB variety and its performance on SL I'd be glad to hear about it but I'll be making my own inquiries.  Also I'll be checking if I can get a better deal on graphics at Best Buy since for our new desktop we got a GT 220M for 50 dollars there.]

EDIT: For grahpics also considering [http://www.compuvest.com/Desc.jsp?iid=1156156](http://www.compuvest.com/Desc.jsp?iid=1156156)

---

### Post by Zorgoth on 2010-01-31
Could someone confirm whether this is ok?

---

### Post by louieb on 2010-01-31
I'd double check the PC3200 memory. Its high density. - not compatible with a lot of machines.   Contact the seller with your motherboard model. They should be able tell if it will work or not. If not they will probably point to memory that will work.

---

### Post by Zorgoth on 2010-01-31
Well it says it runs with 400 MHz - is that the same thing or are the requirements more specific?

can't remember who sold it

---

### Post by Zorgoth on 2010-01-31
How about this?  designed for KV-80 motherboard, mine is KV-80, KV-81, or else KV-82, unsure.

---

### Post by Zorgoth on 2010-01-31
> **Zorgoth said:**
> How about this?  designed for KV-80 motherboard, mine is KV-80, KV-81, or else KV-82, unsure.

oops forgot to link [http://www.buy.com/retail/product.asp?sku=212248571&listingid=52173636](http://www.buy.com/retail/product.asp?sku=212248571&listingid=52173636)

---

