---
title: "Ubuntu Intrepid on sony vaio VGN-TX16C"
date: 2008-12-29
forum: Hardware
---

### Post by ravay on 2008-12-29
I just installed a fresh version of ubuntu 8.10 on a sony vaio VGN-TX16C. Everything works fine except the fn and AV buttons. I checked on the forum but I can't find a solution for my laptop model. Does anybody made them working on te same\similar laptop model?

---

### Post by ravay on 2008-12-30
With **xev** I don't see any event when I press the fn or volume buttons, is this normal?

I tried to do '**sudo setkeycodes e075 235**' but it doesn't help.

I found this link:

[http://blog.prashantv.com/2008/vaio-fs-fn-keys-ubuntu-810/]("http://blog.prashantv.com/2008/vaio-fs-fn-keys-ubuntu-810/")

but I can't find the file **/sys/devices/platform/sony-laptop/fnkey**.

Thank's for your help.

---

### Post by ravay on 2009-01-09
Attached you can find the dsdt file generated following the instructions found on [this]("http://ubuntuforums.org/showthread.php?t=465491&highlight=Sony+Vaio+vgn-n325e") thread and below the dmidecode output.



```
# dmidecode 2.9
SMBIOS 2.3 present.
17 structures occupying 849 bytes.
Table at 0x000D8010.

Handle 0x0000, DMI type 0, 20 bytes
BIOS Information
	Vendor: Phoenix Technologies LTD
	Version: R0051V1
	Release Date: 12/01/2005
	Address: 0xE3930
	Runtime Size: 116432 bytes
	ROM Size: 1024 kB
	Characteristics:
		PCI is supported
		PC Card (PCMCIA) is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		8042 keyboard services are supported (int 9h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		AGP is supported
		Smart battery is supported
		BIOS boot specification is supported
		Function key-initiated network boot is supported

Handle 0x0001, DMI type 1, 25 bytes
System Information
	Manufacturer: Sony Corporation
	Product Name: VGN-TX16C_W
	Version: J0012V3S
	Serial Number: 28199095-9401530
	UUID: C71C1100-DF2D-11D4-8601-0013A98B64ED
	Wake-up Type: Power Switch

Handle 0x0002, DMI type 3, 21 bytes
Chassis Information
	Manufacturer:                       
	Type: Notebook
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
	Number Of Power Cords: Unspecified
	Contained Elements: 0

Handle 0x0003, DMI type 4, 35 bytes
Processor Information
	Socket Designation: N/A
	Type: Central Processor
	Family: Unknown
	Manufacturer: GenuineIntel
	ID: D8 06 00 00 FF FB E9 AF
	Version: Intel(R) Pentium(R) M processor 1.10GHz
	Voltage: 0.9 V
	External Clock: 100 MHz
	Max Speed: 1100 MHz
	Current Speed: 1100 MHz
	Status: Unpopulated
	Upgrade: None
	L1 Cache Handle: 0x0004
	L2 Cache Handle: 0x0005
	L3 Cache Handle: 0x0006
	Serial Number: N/A
	Asset Tag: N/A
	Part Number: N/A

Handle 0x0004, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 32 KB
	Maximum Size: 32 KB
	Supported SRAM Types:
		Burst
		Pipeline Burst
		Asynchronous
	Installed SRAM Type: Asynchronous
	Speed: Unknown
	Error Correction Type: None
	System Type: Other
	Associativity: 8-way Set-associative

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2 Cache
	Configuration: Enabled, Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 2048 KB
	Maximum Size: 2048 KB
	Supported SRAM Types:
		Burst
		Pipeline Burst
		Asynchronous
	Installed SRAM Type: Burst
	Speed: Unknown
	Error Correction Type: None
	System Type: Data
	Associativity: 8-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L3 Cache
	Configuration: Disabled, Not Socketed, Level 3
	Operational Mode: Unknown
	Location: Unknown
	Installed Size: 0 KB
	Maximum Size: 0 KB
	Supported SRAM Types:
		Burst
		Pipeline Burst
		Asynchronous
	Installed SRAM Type: Burst
	Speed: Unknown
	Error Correction Type: None
	System Type: Data
	Associativity: 4-way Set-associative

Handle 0x0007, DMI type 9, 13 bytes
System Slot Information
	Designation: PCCARD1
	Type: 32-bit PC Card (PCMCIA)
	Current Usage: Available
	Length: Other
	ID: Adapter 0, Socket 1
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PC Card-16 is supported
		Cardbus is supported
		Modem ring resume is supported
		PME signal is supported
		Hot-plug devices are supported

Handle 0x0009, DMI type 11, 5 bytes
OEM Strings
	String 1: JPBL-001747
	String 2: FNC-CCIA0ice
	String 3: 4F4P000000006c5c5b87b9c3254f
	String 4: Reserved              
	String 5: Reserved              

Handle 0x000A, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: Unknown
	Maximum Capacity: 2048 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x000B, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x000A
	Error Information Handle: Not Provided
	Total Width: 32 bits
	Data Width: 32 bits
	Size: 512 MB
	Form Factor: SODIMM
	Set: None
	Locator: SODIMM1
	Bank Locator: Bank 0
	Type: DDR
	Type Detail: Unknown
	Speed: 100 MHz (10.0 ns)
	Manufacturer: N/A
	Serial Number: N/A
	Asset Tag: N/A
	Part Number: N/A

Handle 0x000C, DMI type 17, 27 bytes
Memory Device
	Array Handle: 0x000A
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: SODIMM
	Set: None
	Locator: SODIMM2
	Bank Locator: Bank 1
	Type: Unknown
	Type Detail: Unknown
	Speed: 100 MHz (10.0 ns)
	Manufacturer: N/A
	Serial Number: N/A
	Asset Tag: N/A
	Part Number: N/A

Handle 0x000D, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0001FFFFFFF
	Range Size: 512 MB
	Physical Array Handle: 0x000A
	Partition Width: 0

Handle 0x000E, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0001FFFFFFF
	Range Size: 512 MB
	Physical Device Handle: 0x000B
	Memory Array Mapped Address Handle: 0x000D
	Partition Row Position: Unknown
	Interleave Position: Unknown
	Interleaved Data Depth: Unknown

Handle 0x000F, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x0001FFFFC00
	Ending Address: 0x0001FFFFFFF
	Range Size: 1 kB
	Physical Device Handle: 0x000C
	Memory Array Mapped Address Handle: 0x000D
	Partition Row Position: Unknown
	Interleave Position: Unknown
	Interleaved Data Depth: Unknown

Handle 0x0010, DMI type 32, 11 bytes
System Boot Information
	Status: No errors detected

Handle 0x0011, DMI type 127, 4 bytes
End Of Table

```



I hope somebody will reply...


Thank you

---

