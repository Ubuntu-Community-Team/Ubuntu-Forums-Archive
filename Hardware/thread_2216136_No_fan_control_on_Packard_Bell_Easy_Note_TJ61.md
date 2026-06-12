---
title: "No fan control on Packard Bell Easy Note TJ61"
date: 2014-04-10
forum: Hardware
---

### Post by nicolaskokel on 2014-04-10
Dear forum,

I installed MINT 16 64-bit on a Packard Bell TJ61.
Fan is running continuously.
I searched for a solution, installed LM sensors, which efficiently controlled the fan speed but only after one reboot.
During the next reboot, the graphic drivers could not be loaded since fglrx proprietary drivers were installed and the graphic card version is no longer supported.
I uninstalled and purged fglrx and could reboot, but without fan control.
Is there a workaround to solve this continuous fan noise?

PS: found a similar thread for a similar model here but with no solution:
[http://ubuntuforums.org/showthread.php?t=1631244](http://ubuntuforums.org/showthread.php?t=1631244)

$ sudo sensors 
> acpitz-virtual-0
Adapter: Virtual device
temp1:        +91.0°C  (crit = +100.0°C)
temp2:        +84.0°C  (crit = +100.0°C)
k10temp-pci-00c3
Adapter: PCI adapter
temp1:        +88.2°C  (high = +70.0°C)


$ sudo lshw -c display
 >  *-display               
       description: VGA compatible controller
       product: RS780M [Mobility Radeon HD 3200]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:18 memory:d0000000-dfffffff ioport:9000(size=256) memory:cfdf0000-cfdfffff memory:cfe00000-cfefffff

$ sudo dmidecode -q


> BIOS Information
	Vendor: Phoenix Technologies LTD
	Version: V1.08          
	Release Date: 06/15/2009
	Address: 0xE4A30
	Runtime Size: 112080 bytes
	ROM Size: 1024 kB
	Characteristics:
		PCI is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		ESCD support is available
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		BIOS boot specification is supported
		Targeted content distribution is supported


System Information
	Manufacturer: Packard Bell   
	Product Name: EasyNote TJ61                  
	Version: 0100           
	Serial Number: LXBFC0X002932B5D442200        
	UUID: D55058A0-85E9-11DE-8EFB-AA512A71D834
	Wake-up Type: Power Switch
	SKU Number: Not Specified
	Family: Not Specified


Base Board Information
	Manufacturer: Packard Bell   
	Product Name: SJV50PU                        
	Version: Rev            
	Serial Number: LXBFC0X002932B5D442200        


Chassis Information
	Manufacturer: Parkard Bell   
	Type: Notebook
	Lock: Not Present
	Version: N/A            
	Serial Number: None           
	Asset Tag:                                 
	Boot-up State: Unknown
	Power Supply State: Unknown
	Thermal State: Unknown
	Security Status: Unknown
	OEM Information: 0x00000000


Processor Information
	Socket Designation: Socket S1G2
	Type: Central Processor
	Family: Athlon Dual-Core
	Manufacturer: AMD
	ID: 31 0F 20 00 FF FB 8B 17
	Signature: Family 17, Model 3, Stepping 1
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
		FXSR (FXSAVE and FXSTOR instructions supported)
		SSE (Streaming SIMD extensions)
		SSE2 (Streaming SIMD extensions 2)
		HTT (Multi-threading)
	Version: AMD Athlon(tm) X2 Dual-Core QL-65
	Voltage: 1.1 V
	External Clock: 200 MHz
	Max Speed: 4000 MHz
	Current Speed: 2100 MHz
	Status: Populated, Enabled
	Upgrade: Other
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified
	Core Count: 2
	Core Enabled: 2
	Thread Count: 2
	Characteristics:
		64-bit capable


Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 64 kB
	Maximum Size: 64 kB
	Supported SRAM Types:
		Burst
		Pipeline Burst
		Asynchronous
	Installed SRAM Type: Asynchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown


Cache Information
	Socket Designation: H0 L2 Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 1024 kB
	Maximum Size: 2048 kB
	Supported SRAM Types:
		Burst
		Pipeline Burst
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unified
	Associativity: Unknown


Port Connector Information
	Internal Reference Designator: J28
	Internal Connector Type: None
	External Reference Designator: COM A
	External Connector Type: DB-9 male
	Port Type: Serial Port 16550A Compatible


Port Connector Information
	Internal Reference Designator: J28
	Internal Connector Type: None
	External Reference Designator: Parallel
	External Connector Type: DB-25 female
	Port Type: Parallel Port ECP/EPP


Port Connector Information
	Internal Reference Designator: J28
	Internal Connector Type: None
	External Reference Designator: Video
	External Connector Type: DB-15 female
	Port Type: Video Port


Port Connector Information
	Internal Reference Designator: J33
	Internal Connector Type: None
	External Reference Designator: Keyboard
	External Connector Type: Circular DIN-8 male
	Port Type: Keyboard Port


Port Connector Information
	Internal Reference Designator: J33
	Internal Connector Type: None
	External Reference Designator: PS/2 Mouse
	External Connector Type: Circular DIN-8 male
	Port Type: Keyboard Port


Port Connector Information
	Internal Reference Designator: J31
	Internal Connector Type: None
	External Reference Designator: USB 1
	External Connector Type: Access Bus (USB)
	Port Type: USB


Port Connector Information
	Internal Reference Designator: J32
	Internal Connector Type: None
	External Reference Designator: USB 2
	External Connector Type: Access Bus (USB)
	Port Type: USB


Port Connector Information
	Internal Reference Designator: J32
	Internal Connector Type: None
	External Reference Designator: USB 3
	External Connector Type: Access Bus (USB)
	Port Type: USB


Port Connector Information
	Internal Reference Designator: J31
	Internal Connector Type: None
	External Reference Designator: USB 4
	External Connector Type: Access Bus (USB)
	Port Type: USB


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
	Designation: MINI PCI
	Type: 32-bit PCI
	Current Usage: Unknown
	Length: Other
	ID: 0
	Characteristics:
		5.0 V is provided
		3.3 V is provided
		PME signal is supported


On Board Device Information
	Type: Video
	Status: Disabled
	Description: ATI RS690M


On Board Device Information
	Type: Sound
	Status: Disabled
	Description: ESS 1869


OEM Strings
	String 1:  
	String 2:  
	String 3:  


System Configuration Options
	Option 1: J13 1-2 Normal Operation, 2-3 Clear CMOS


BIOS Language Information
	Language Description Format: Abbreviated
	Installable Languages: 1
		enUS
	Currently Installed Language: enUS


System Event Log
	Area Length: 16 bytes
	Header Start Offset: 0x0000
	Header Length: 16 bytes
	Data Start Offset: 0x0010
	Access Method: General-purpose non-volatile data functions
	Access Address: 0x0000
	Status: Valid, Not Full
	Change Token: 0x00000001
	Header Format: Type 1
	Supported Log Type Descriptors: 3
	Descriptor 1: POST error
	Data Format 1: POST results bitmap
	Descriptor 2: Single-bit ECC memory error
	Data Format 2: Multiple-event
	Descriptor 3: Multi-bit ECC memory error
	Data Format 3: Multiple-event


Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 8 GB
	Number Of Devices: 4


Memory Device
	Total Width: 128 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: 1
	Locator: S1
	Bank Locator: DIMM1
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: Not Specified
	Part Number: Not Specified


Memory Device
	Total Width: 128 bits
	Data Width: 64 bits
	Size: 2048 MB
	Form Factor: DIMM
	Set: 2
	Locator: S2
	Bank Locator: DIMM2
	Type: DDR2
	Type Detail: Synchronous
	Speed: 667 MHz
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
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Partition Width: 2


Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0007FFFFFFF
	Range Size: 2 GB
	Partition Row Position: 2
	Interleave Position: 1
	Interleaved Data Depth: 6


System Boot Information
	Status: <OUT OF SPEC>


---

### Post by Vinay Balraj on 2014-04-10
Hi, @nicolaskokel, check to see if there are any BIOS updates available for your computer, I had the same issue on my Dell and after a lot of googling, I had observed that with most manufacturers, the continuous fan spin at max speeds can be eliminated after a BIOS update, which couldn't be solved by LM sensors either. I did the same, and now on my laptop the fan is very quite and on windows where I used to get 6 hours of battery backup, now I get 7.30 after that fix.

---

### Post by Mark Phelps on 2014-04-10
I strongly advise AGAINST doing a BIOS update unless BOTH of the following are true:
1)  You have a way of saving off the current BIOS to a medium that could be use later to restore if, if that becomes necessary
2)  You have a way of restoring a saved BIOS without having to boot into an OS.

A failed BIOS update is a surefire way of turning a working PC into a "brick"!

---

### Post by monkeybrain20122 on 2014-04-10
If you have a recent enough kernel (> 3.11?) you can try this. 
Open the file /etc/default/grub and change the line 
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" 
to
> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.dpm=1" 

Save and close the file, then run in the terminal
```
sudo update-grub
```
And then reboot. It may fix your problem.

---

### Post by nicolaskokel on 2014-04-13
The grub line on my system is :

> GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

**should I insert **
> [COLOR=#000000][I]
radeon.dpm=1[/I][/COLOR]
**anyway?**

The problem is in fact NOT that there is no fan control, since when the labtop starts the fan does not run up immediately, or if left quiet for some time, the fan eventually runs down.
It is definitely a graphic driver issue, because proprietary drivers can not be used since my graphic adapter is not supported and there is therefore no energy management with the standard linux drivers.
I have now followed the instructions provided here : [http://doc.ubuntu-fr.org/radeon](http://doc.ubuntu-fr.org/radeon) and typed the commands from section 2.1. and 2.2.
Anyway I did not do the commands from section 3.1 since I had previously purged any fglrx install, and since my graphic server is dpm, and not lightdm.
**After reboot, I checked that there is no xorg.conf file in the /etc/x11/ folder (checked with CTRL+H as well), and I wonder if this is necessary to make the open source Radeon drivers work on my system? **
If yes, how do I do this with dpm as a graphic server, simply by replacing "lightdm" with "dpm" in the code line?

Thanks a lot,
Nicolas

---

### Post by nicolaskokel on 2014-04-15
bump

---

