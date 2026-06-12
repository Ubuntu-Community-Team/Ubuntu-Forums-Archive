---
title: "Lenovo x121e i3 Linux Hardware Compatability"
date: 2011-12-13
forum: Hardware
---

### Post by connect404 on 2011-12-13
This thread's aim is to provide a single up to date source for hardware compatibility for the Lenovo x121e (in particular the i3 variant) laptop. There are a [number of detailed threads]("http://forums.overclockers.co.uk/showthread.php?t=18295203") around that already cover the generals about the hardware, but don't specifically deal with Ubuntu/Linux support. Please post any updates or revisions and I will keep this initial post up to date

**Current BIOS/CPU:**
```
daniel@racerx:~$ sudo dmidecode | grep Version
	Version: Intel(R) Core(TM) i3-2367M CPU @ 1.40GHz
	Version: 8QET53WW (1.14 )
	Version: ThinkPad X121e
```

**Base OS:**
```
daniel@racerx:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
daniel@racerx:~$ uname -a
Linux racerx 3.0.0-14-generic #20-Ubuntu SMP Fri Oct 7 14:56:25 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

[B]Legend:
[COLOR=Green]100% Supported (maybe with a patch)[/COLOR]
[COLOR=DarkOrange]A number of small bugs are present[/COLOR]
[COLOR=Red]Not Working[/COLOR]
[COLOR=Blue]Untested[/COLOR]
[/B]



**[COLOR=Green][SIZE=2]BIOS[/SIZE][/COLOR]**
[LIST]
[*]UEFI Boot support needs to be disabled in the BIOS for ubuntu 11.10
[*]Excellent BIOS with very very granular control for I/O, ATA Passwords, extra devices and CPU options
[/LIST]



**[COLOR=Green][SIZE=2]Webcam[/SIZE][/COLOR]**
[LIST]
[*]Full Native Support
[*]Skype, Cheese, etc all work 100%
[/LIST]



**[SIZE=2][COLOR=Green]Suspend to RAM / Suspend to Disk[/SIZE][/COLOR]**
[LIST]
[*]The laptop goes in and out of sleep/hibernate cleanly.
[*]No syslog error message or abnormnal behaviour after resume
[*]Wifi/Bluetooth returns to previous state on resume.
[/LIST]



**[SIZE=2][COLOR=DarkOrange]Multi Card Reader[/SIZE][/COLOR]**
[LIST]
[*]When returning from suspend the card reader no longer functions. 
[*]Tested OK with an SD & SDHC card only.
[COLOR=Blue][*] Booting from Memory cards need to be tested[/COLOR]
[/LIST]



**[SIZE=2][COLOR=Green]Bluetooth[/SIZE][/COLOR]**
[LIST]
[*]Some inital issues with the card being hard blocked. Seems after an initial ubuntu install the card becomes blocked and you need to "Restore Defaults" in the BIOS and then reboot and things will magically work! [This launchpad bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/812866") covers it in detail.
[*]After the initlal problems rfkill now shows the devices hard unblocked and switching via keyboard or software toggles soft block properly:
[/LIST]
```
daniel@racerx:~$ sudo rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```



**[SIZE=2][COLOR=Blue]Fingerprint reader[/SIZE][/COLOR]**
[LIST]
[*]Untested
[/LIST]



**[SIZE=2][COLOR=Green]Intel Centrino-N Wifi[/SIZE][/COLOR]**
[LIST]
[*]Full WEP/WPA/WPA2 support
[COLOR=Blue][*]Max Speed tests yet to be completed[/COLOR]
[/LIST]



**[SIZE=2][COLOR=Blue]Broadcom 1x1 B/G/N Wifi[/SIZE][/COLOR]**
[LIST]
[*]Untested but web reports seem to indicate it works
[*]Speed test & 'lspci -v' results needed
[/LIST]



**[SIZE=2][COLOR=Blue]Broadcom 2x2 A/B/G/N Wifi[/SIZE][/COLOR]**
[LIST]
[*]Untested but web reports seem to indicate it works
[*]Speed test & 'lspci -v' results needed
[/LIST]



**[SIZE=2][COLOR=DarkOrange]Mechanical Hard Drive[/SIZE][/COLOR]**
[LIST][COLOR=green][*]ACHI Support in BIOS for drives[/COLOR]
[*] The hard drive accelerometer/impact sensor/protection system is not supported by hdapsd.
[/LIST]
```
daniel@racerx:~$ sudo hdapsd -d sda
Tue Dec 13 18:31:19 2011: Starting hdapsd
Tue Dec 13 18:31:19 2011: Could not find a suitable interface
```



**[SIZE=2][COLOR=Green] Touchpad & Keyboard Nipple[/SIZE][/COLOR]**
[LIST]
[*]Works well with Synaptic v1.4 included in base Ubuntu 11.10
[*]Two finger scrolling works by default
[*]Tap to click by default
[*]Two finger tap to right click works by default
[*]Touchpad lockout when typing works by default
[*]Keyboard Nipple and 3 buttons work 100%
[/LIST]



**[SIZE=2][COLOR=Green]Keyboard[/SIZE][/COLOR]**
[LIST]
[*]F1-F12 are the default action, with Fn being secondary
[*]Fn-* Mute, Volume, Brightness, Sleep work
[*]Fn-F5 keys work, but switch ALL radios to alternate state
[*]I had to unassign, then reassign the play/pause key to a function before it worked correctly.
[COLOR=Blue][*]Fn-F3 untested[/COLOR]
[COLOR=Blue][*]Fn-F6 untested[/COLOR]
[COLOR=Blue][*]Fn-F7 untested[/COLOR]
[/LIST]



**[SIZE=2][COLOR=Green]Sleep&Charge USB[/COLOR][/SIZE]**
[LIST]
[*]When enabled in the BIOS the yellow USB port will charge even when the laptop is either suspended or off
[/LIST]



**[SIZE=2][COLOR=Blue]TPM Module[/SIZE]**[LIST][*]Untested in Ubuntu as yet, but hardware detected[/LIST][/COLOR]


**[SIZE=2][COLOR=Blue]NIC[/SIZE]**
[LIST]
[*]Untested in Ubuntu as yet, but hardware detected
[/LIST][/COLOR]



**[SIZE=2][COLOR=Green]LCD[/COLOR][/SIZE]**
[LIST]
[*]Brightness works 100% and scale is fairly linear.
[*]Autodimm works
[*]After resume the bightness works 100%
[/LIST]



[B][SIZE=2][COLOR=Green]Intel HD3000
[/COLOR][/SIZE][/B]
[LIST]
[*]Intel video card is fully supported.
[*]Compiz is on by default and all desktop effects work great
[*]Full SD & HD (720p & 1080p) playback works 100%
[*]VGA & HDMI outputs can be configured as secondary or mirrored devices and detect/displays correctly.
[*]Have had this plugged into both a TV and LCD monitor and everything works flawlessly.
[/LIST]



**[SIZE=2][COLOR=Green]Intel HD Audio[/COLOR][/SIZE]**
[LIST]
[*]Sound playback through speakers works
[*]HDMI audio output works however it does not autoswtich and needs to be manually selected in the "Sound Settings" menu. After removal of the HDMI cable the output source needs to be changed back to "Analogue Duplex"
[*]Headset port switches from speakers to headphones and back correctly
[*]Headset port supports iPhone style headsets and mic input is passed through seamlessly.
[COLOR=Blue][*]Digital 5.1 audio options in "Sound Menu" output tab need to be tested[/COLOR]
[/LIST]



**[SIZE=2][COLOR=Green]Battery[/COLOR][/SIZE]**
[LIST]
[*]65W Battery Stats are detected and displayed correctly
[*]Depletion rate seems to be accurate
[/LIST]

---

### Post by connect404 on 2011-12-13
dmidecode
```

# dmidecode 2.9
SMBIOS 2.6 present.
72 structures occupying 2643 bytes.
Table at 0x000E0830.

Handle 0x0000, DMI type 134, 16 bytes
OEM-specific Type
	Header and Data:
		86 10 00 00 00 53 54 4D 20 01 01 00 00 03 01 02
	Strings:
		TPM INFO
		System Reserved

Handle 0x0001, DMI type 4, 42 bytes
Processor Information
	Socket Designation: CPU
	Type: Central Processor
	Family: <OUT OF SPEC>
	Manufacturer: Intel(R) Corporation
	ID: A7 06 02 00 FF FB EB BF
	Version: Intel(R) Core(TM) i3-2367M CPU @ 1.40GHz
	Voltage: 1.2 V
	External Clock: 100 MHz
	Max Speed: 1400 MHz
	Current Speed: 1400 MHz
	Status: Populated, Enabled
	Upgrade: ZIF Socket
	L1 Cache Handle: 0x0002
	L2 Cache Handle: 0x0003
	L3 Cache Handle: 0x0004
	Serial Number: Not Supported by CPU
	Asset Tag: TBD By OEM
	Part Number: TBD By OEM
	Core Count: 2
	Core Enabled: 2
	Thread Count: 4
	Characteristics:
		64-bit capable

Handle 0x0002, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1-Cache
	Configuration: Enabled, Not Socketed, Level 1
	Operational Mode: Write Through
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

Handle 0x0003, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2-Cache
	Configuration: Enabled, Not Socketed, Level 2
	Operational Mode: Write Through
	Location: Internal
	Installed Size: 256 KB
	Maximum Size: 256 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Data
	Associativity: 8-way Set-associative

Handle 0x0004, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L3-Cache
	Configuration: Enabled, Not Socketed, Level 3
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 3072 KB
	Maximum Size: 3072 KB
	Supported SRAM Types:
		Synchronous
	Installed SRAM Type: Synchronous
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: <OUT OF SPEC>

Handle 0x0005, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 16 GB
	Error Information Handle: Not Provided
	Number Of Devices: 4

Handle 0x0006, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x0005
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 4096 MB
	Form Factor: SODIMM
	Set: None
	Locator: ChannelA-DIMM0
	Bank Locator: BANK 0
	Type: <OUT OF SPEC>
	Type Detail: Synchronous
	Speed: 1333 MHz (0.8 ns)
	Manufacturer: 859B
	Serial Number: 00000000
	Asset Tag: 9876543210
	Part Number: CT51264BC1339.M16F

Handle 0x0007, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x000FFFFFFFF
	Range Size: 4 GB
	Physical Device Handle: 0x0006
	Memory Array Mapped Address Handle: 0x000C
	Partition Row Position: Unknown
	Interleave Position: 1
	Interleaved Data Depth: 2

Handle 0x0008, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x0005
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: ChannelA-DIMM1
	Bank Locator: BANK 1
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: 9876543210
	Part Number: Not Specified

Handle 0x0009, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x0005
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 4096 MB
	Form Factor: SODIMM
	Set: None
	Locator: ChannelB-DIMM0
	Bank Locator: BANK 2
	Type: <OUT OF SPEC>
	Type Detail: Synchronous
	Speed: 1333 MHz (0.8 ns)
	Manufacturer: 859B
	Serial Number: 00000000
	Asset Tag: 9876543210
	Part Number: CT51264BC1339.M16F

Handle 0x000A, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00100000000
	Ending Address: 0x001FFFFFFFF
	Range Size: 4 GB
	Physical Device Handle: 0x0009
	Memory Array Mapped Address Handle: 0x000C
	Partition Row Position: Unknown
	Interleave Position: 2
	Interleaved Data Depth: 2

Handle 0x000B, DMI type 17, 28 bytes
Memory Device
	Array Handle: 0x0005
	Error Information Handle: Not Provided
	Total Width: Unknown
	Data Width: Unknown
	Size: No Module Installed
	Form Factor: DIMM
	Set: None
	Locator: ChannelB-DIMM1
	Bank Locator: BANK 3
	Type: Unknown
	Type Detail: None
	Speed: Unknown
	Manufacturer: Not Specified
	Serial Number: Not Specified
	Asset Tag: 9876543210
	Part Number: Not Specified

Handle 0x000C, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x001FFFFFFFF
	Range Size: 8 GB
	Physical Array Handle: 0x0005
	Partition Width: 0

Handle 0x000D, DMI type 129, 8 bytes
OEM-specific Type
	Header and Data:
		81 08 0D 00 01 01 02 01
	Strings:
		Intel_ASF
		Intel_ASF_001

Handle 0x000E, DMI type 131, 64 bytes
OEM-specific Type
	Header and Data:
		83 40 0E 00 31 00 00 00 00 00 00 00 00 00 00 00
		F8 00 49 1C FF FF FF FF 09 E0 00 00 01 00 07 00
		29 04 0A 00 00 00 00 00 C8 00 FF FF 00 00 00 00
		00 00 00 00 F6 00 00 00 76 50 72 6F 00 00 00 00

Handle 0x000F, DMI type 134, 13 bytes
OEM-specific Type
	Header and Data:
		86 0D 0F 00 01 05 10 20 00 00 00 00 00

Handle 0x0010, DMI type 0, 24 bytes
BIOS Information
	Vendor: LENOVO
	Version: 8QET53WW (1.14 )
	Release Date: 10/25/2011
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 4096 kB
	Characteristics:
		PCI is supported
		PNP is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		EDD is supported
		3.5"/720 KB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		CGA/mono video services are supported (int 10h)
		ACPI is supported
		USB legacy is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
	BIOS Revision: 24.216
	Firmware Revision: 1.9

Handle 0x0011, DMI type 1, 27 bytes
System Information
	Manufacturer: LENOVO
	Product Name: 3045CTO
	Version: ThinkPad X121e
	Serial Number: LR1DKB1
	UUID: 01D0992F-7B50-CB11-AA57-8746F7788587
	Wake-up Type: Power Switch
	SKU Number: ThinkPad X121e
	Family: <BAD INDEX>

Handle 0x0012, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: LENOVO
	Product Name: 3045CTO
	Version: Not Available
	Serial Number: 1ZKA71BM056
	Asset Tag: Not Available
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Not Available
	Chassis Handle: 0x0000
	Type: Unknown
	Contained Object Handles: 0

Handle 0x0013, DMI type 3, 21 bytes
Chassis Information
	Manufacturer: LENOVO
	Type: Notebook
	Lock: Not Present
	Version: Not Available
	Serial Number: LR1DKB1
	Asset Tag: No Asset Information
	Boot-up State: Unknown
	Power Supply State: Unknown
	Thermal State: Unknown
	Security Status: Unknown
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: Unspecified
	Contained Elements: 0

Handle 0x0014, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: Keyboard
	External Connector Type: PS/2
	Port Type: Keyboard Port

Handle 0x0015, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: Mouse
	External Connector Type: PS/2
	Port Type: Mouse Port

Handle 0x0016, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: Other
	External Reference Designator: COM 1
	External Connector Type: None
	Port Type: Serial Port 16550A Compatible

Handle 0x0017, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 1#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0018, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 2#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0019, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 3#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x001A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 4#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x001B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 5#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x001C, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 6#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x001D, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 7#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x001E, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 8#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x001F, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 9#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0020, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 10#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0021, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 11#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0022, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 12#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0023, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 13#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0024, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: USB2.0 - 14#
	External Connector Type: Access Bus (USB)
	Port Type: USB

Handle 0x0025, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: Ethernet
	External Connector Type: RJ-45
	Port Type: Network Port

Handle 0x0026, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: SATA Port 1 J8J1
	Internal Connector Type: SAS/SATA Plug Receptacle
	External Reference Designator: None
	External Connector Type: None
	Port Type: SATA

Handle 0x0027, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: SATA Port 2 J7G1
	Internal Connector Type: SAS/SATA Plug Receptacle
	External Reference Designator: None
	External Connector Type: None
	Port Type: SATA

Handle 0x0028, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: SATA Port 3(ODD) J9E7
	Internal Connector Type: SAS/SATA Plug Receptacle
	External Reference Designator: None
	External Connector Type: None
	Port Type: SATA

Handle 0x0029, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: eSATA Port 1 J6J1
	External Connector Type: SAS/SATA Plug Receptacle
	Port Type: SATA

Handle 0x002A, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: eSATA Port 2 J7J1
	External Connector Type: SAS/SATA Plug Receptacle
	Port Type: SATA

Handle 0x002B, DMI type 8, 9 bytes
Port Connector Information
	Internal Reference Designator: None
	Internal Connector Type: None
	External Reference Designator: SATA Port 6(Docking)
	External Connector Type: SAS/SATA Plug Receptacle
	Port Type: SATA

Handle 0x002C, DMI type 9, 17 bytes
System Slot Information
	Designation: PEG Gen1/Gen2 X16
	Type: x16 <OUT OF SPEC>
	Current Usage: Available
	Length: Long
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x002D, DMI type 9, 17 bytes
System Slot Information
	Designation: PCI-Express 1 X1
	Type: x1 PCI Express
	Current Usage: Available
	Length: Short
	ID: 1
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x002E, DMI type 9, 17 bytes
System Slot Information
	Designation: PCI-Express 2 X1
	Type: x1 PCI Express
	Current Usage: In Use
	Length: Short
	ID: 2
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x002F, DMI type 9, 17 bytes
System Slot Information
	Designation: PCI-Express 3 X1
	Type: x1 PCI Express
	Current Usage: In Use
	Length: Short
	ID: 3
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x0030, DMI type 9, 17 bytes
System Slot Information
	Designation: PCI-Express 4 X1
	Type: x1 PCI Express
	Current Usage: Available
	Length: Short
	ID: 4
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x0031, DMI type 9, 17 bytes
System Slot Information
	Designation: PCI-Express 5 X1
	Type: x1 PCI Express
	Current Usage: Available
	Length: Short
	ID: 5
	Characteristics:
		3.3 V is provided
		Opening is shared
		PME signal is supported

Handle 0x0032, DMI type 10, 6 bytes
On Board Device Information
	Type: Video
	Status: Enabled
	Description: Intel(R) Extreme Graphics 3 Controller

Handle 0x0033, DMI type 10, 6 bytes
On Board Device Information
	Type: Sound
	Status: Enabled
	Description: Intel(R) Azalia Audio Device

Handle 0x0034, DMI type 11, 5 bytes
OEM Strings
	String 1: This is the Intel HuronRiver CRB Platform

Handle 0x0035, DMI type 12, 5 bytes
System Configuration Options

Handle 0x0036, DMI type 13, 22 bytes
BIOS Language Information
	Installable Languages: 4
		en-US
		fr-FR
		ja-JP
		ko-KR
	Currently Installed Language: en-US

Handle 0x0037, DMI type 22, 26 bytes
Portable Battery
	Location: Rear
	Manufacturer: Intel Corp.
	Manufacture Date: 2008
	Serial Number: 1.0
	Name: Smart Battery
	Design Capacity: Unknown
	Design Voltage: Unknown
	SBDS Version: V1.0
	Maximum Error: Unknown
	SBDS Chemistry: Lithium-Ion
	OEM-specific Information: 0x00000000

Handle 0x0038, DMI type 32, 11 bytes
System Boot Information
	Status: No errors detected

Handle 0x0039, DMI type 135, 10 bytes
OEM-specific Type
	Header and Data:
		87 0A 39 00 54 50 07 03 01 07

Handle 0x003A, DMI type 131, 22 bytes
OEM-specific Type
	Header and Data:
		83 16 3A 00 01 00 00 00 00 00 00 00 00 00 00 00
		00 00 00 00 00 01
	Strings:
		TVT-Enablement

Handle 0x003B, DMI type 135, 34 bytes
OEM-specific Type
	Header and Data:
		87 22 3B 00 54 50 07 04 01 06 01 01 02 00 02 01
		02 00 03 01 02 00 04 01 02 00 05 01 02 00 06 01
		02 00

Handle 0x003C, DMI type 200, 7 bytes
OEM-specific Type
	Header and Data:
		C8 07 3C 00 01 02 03
	Strings:
		152D
		FL9 
		BQ3C61

Handle 0x003D, DMI type 18, 23 bytes
32-bit Memory Error Information
	Type: OK
	Granularity: Unknown
	Operation: Unknown
	Vendor Syndrome: Unknown
	Memory Array Address: Unknown
	Device Address: Unknown
	Resolution: Unknown

Handle 0x003E, DMI type 21, 7 bytes
Built-in Pointing Device
	Type: Mouse
	Interface: PS/2
	Buttons: 2

Handle 0x003F, DMI type 23, 13 bytes
System Reset
	Status: Disabled
	Watchdog Timer: Present
	Boot Option: Do Not Reboot
	Boot Option On Limit: Do Not Reboot
	Reset Count: Unknown
	Reset Limit: Unknown
	Timer Interval: Unknown
	Timeout: Unknown

Handle 0x0040, DMI type 24, 5 bytes
Hardware Security
	Power-On Password Status: Unknown
	Keyboard Password Status: Unknown
	Administrator Password Status: Unknown
	Front Panel Reset Status: Unknown

Handle 0x0041, DMI type 27, 14 bytes
Cooling Device
	Type: Unknown
	Status: Unknown
	OEM-specific Information: 0x00000090
	Nominal Speed: Unknown Or Non-rotating

Handle 0x0042, DMI type 39, 22 bytes
System Power Supply
	Location: TBD by ODM
	Name: TBD by ODM
	Manufacturer: TBD by ODM
	Serial Number: TBD by ODM
	Asset Tag: TBD by ODM
	Model Part Number: TBD by ODM
	Revision: 1.0
	Max Power Capacity: Unknown
	Status: Present, OK
	Type: Battery
	Input Voltage Range Switching: Other
	Plugged: Yes
	Hot Replaceable: Yes

Handle 0x0043, DMI type 135, 36 bytes
OEM-specific Type
	Header and Data:
		87 24 43 00 54 50 07 02 42 41 59 20 49 2F 4F 20
		02 00 02 00 00 00 00 88 40 96 40 FF 00 00 00 88
		40 96 40 00

Handle 0x0044, DMI type 133, 5 bytes
OEM-specific Type
	Header and Data:
		85 05 44 00 01
	Strings:
		KHOIHGIUCCHHII

Handle 0x0045, DMI type 15, 29 bytes
System Event Log
	Area Length: 18 bytes
	Header Start Offset: 0x0000
	Header Length: 16 bytes
	Data Start Offset: 0x0010
	Access Method: General-purpose non-volatile data functions
	Access Address: 0x00F0
	Status: Valid, Not Full
	Change Token: 0x00000000
	Header Format: Type 1
	Supported Log Type Descriptors: 3
	Descriptor 1: POST error
	Data Format 1: POST results bitmap
	Descriptor 2: Single-bit ECC memory error
	Data Format 2: Multiple-event
	Descriptor 3: Multi-bit ECC memory error
	Data Format 3: Multiple-event

Handle 0x0046, DMI type 135, 18 bytes
OEM-specific Type
	Header and Data:
		87 12 46 00 54 50 07 01 01 00 00 00 00 00 00 00
		00 00

Handle 0xFEFF, DMI type 127, 4 bytes
End Of Table
```

lspci -v
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
	Subsystem: Lenovo Device 21ed
	Flags: bus master, fast devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Lenovo Device 21ed
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at d0000000 (64-bit, non-prefetchable) [size=4M]
	Memory at c0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4000 [size=64]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [d0] Power Management version 2
	Capabilities: [a4] PCI Advanced Features
	Kernel driver in use: i915
	Kernel modules: i915

00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: Lenovo Device 21ed
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at d1605000 (64-bit, non-prefetchable) [size=16]
	Capabilities: [50] Power Management version 3
	Capabilities: [8c] MSI: Enable- Count=1/1 Maskable- 64bit+
	Kernel driver in use: mei
	Kernel modules: mei

00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Lenovo Device 21ed
	Flags: bus master, medium devsel, latency 0, IRQ 16
	Memory at d160a000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: Lenovo Device 21ed
	Flags: bus master, fast devsel, latency 0, IRQ 43
	Memory at d1600000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
	Capabilities: [100] Virtual Channel
	Capabilities: [130] Root Complex Link
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Lenovo Device 21ed
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
	Memory behind bridge: d1500000-d15fffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Lenovo Device 21ed
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=03, subordinate=07, sec-latency=0
	I/O behind bridge: 00003000-00003fff
	Memory behind bridge: d0d00000-d14fffff
	Prefetchable memory behind bridge: 00000000d0400000-00000000d0bfffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Lenovo Device 21ed
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	I/O behind bridge: 00002000-00002fff
	Memory behind bridge: d0c00000-d0cfffff
	Capabilities: [40] Express Root Port (Slot+), MSI 00
	Capabilities: [80] MSI: Enable- Count=1/1 Maskable- 64bit-
	Capabilities: [90] Subsystem: Lenovo Device 21ed
	Capabilities: [a0] Power Management version 2
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
	Subsystem: Lenovo Device 21ed
	Flags: bus master, medium devsel, latency 0, IRQ 23
	Memory at d1609000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: [50] Power Management version 2
	Capabilities: [58] Debug port: BAR=1 offset=00a0
	Capabilities: [98] PCI Advanced Features
	Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
	Subsystem: Lenovo Device 21ed
	Flags: bus master, medium devsel, latency 0
	Capabilities: [e0] Vendor Specific Information: Len=0c <?>
	Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04) (prog-if 01 [AHCI 1.0])
	Subsystem: Lenovo Device 21ed
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40
	I/O ports at 4088 [size=8]
	I/O ports at 4094 [size=4]
	I/O ports at 4080 [size=8]
	I/O ports at 4090 [size=4]
	I/O ports at 4060 [size=32]
	Memory at d1608000 (32-bit, non-prefetchable) [size=2K]
	Capabilities: [80] MSI: Enable+ Count=1/1 Maskable- 64bit-
	Capabilities: [70] Power Management version 3
	Capabilities: [a8] SATA HBA v1.0
	Capabilities: [b0] PCI Advanced Features
	Kernel driver in use: ahci
	Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
	Subsystem: Lenovo Device 21ed
	Flags: medium devsel, IRQ 11
	Memory at d1604000 (64-bit, non-prefetchable) [size=256]
	I/O ports at efa0 [size=32]
	Kernel modules: i2c-i801

02:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
	Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
	Flags: bus master, fast devsel, latency 0, IRQ 41
	Memory at d1500000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 74-e5-0b-ff-ff-86-ec-ee
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn

03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
	Subsystem: Lenovo Device 21ed
	Flags: bus master, fast devsel, latency 0, IRQ 18
	Memory at d0d00000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: [40] Power Management version 3
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
	Capabilities: [70] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number 00-00-00-01-00-4c-e0-00
	Kernel driver in use: rts_pstor
	Kernel modules: rts_pstor

08:00.0 Ethernet controller: Atheros Communications AR8151 v2.0 Gigabit Ethernet (rev c0)
	Subsystem: Lenovo Device 21f2
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at d0c00000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at 2000 [size=128]
	Capabilities: [40] Power Management version 3
	Capabilities: [48] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [58] Express Endpoint, MSI 00
	Capabilities: [6c] Vital Product Data
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [180] Device Serial Number ff-18-6c-42-04-7d-7b-ff
	Kernel driver in use: atl1c
	Kernel modules: atl1c
```

lsusb -v
```


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.00
  iManufacturer           3 Linux 3.0.0-14-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1a.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0507 highspeed power suspend enable connect
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  idVendor           0x1d6b Linux Foundation
  idProduct          0x0002 2.0 root hub
  bcdDevice            3.00
  iManufacturer           3 Linux 3.0.0-14-generic ehci_hcd
  iProduct                2 EHCI Host Controller
  iSerial                 1 0000:00:1d.0
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0004  1x 4 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             2
  wHubCharacteristic 0x000a
    No power switching (usb 1.0)
    Per-port overcurrent protection
  bPwrOn2PwrGood       10 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0507 highspeed power suspend enable connect
   Port 2: 0000.0100 power
Device Status:     0x0003
  Self Powered
  Remote Wakeup Enabled

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x8087 Intel Corp.
  idProduct          0x0024 Integrated Rate Matching Hub
  bcdDevice            0.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x0009
    Per-port power switching
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0100 power
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         1 Single TT
  bMaxPacketSize0        64
  idVendor           0x8087 Intel Corp.
  idProduct          0x0024 Integrated Rate Matching Hub
  bcdDevice            0.00
  iManufacturer           0 
  iProduct                0 
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           25
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0xe0
      Self Powered
      Remote Wakeup
    MaxPower                0mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass         9 Hub
      bInterfaceSubClass      0 Unused
      bInterfaceProtocol      0 Full speed (or root) hub
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0001  1x 1 bytes
        bInterval              12
Hub Descriptor:
  bLength               9
  bDescriptorType      41
  nNbrPorts             6
  wHubCharacteristic 0x0009
    Per-port power switching
    Per-port overcurrent protection
    TT think time 8 FS bits
  bPwrOn2PwrGood       50 * 2 milli seconds
  bHubContrCurrent      0 milli Ampere
  DeviceRemovable    0x00
  PortPwrCtrlMask    0xff
 Hub Port Status:
   Port 1: 0000.0100 power
   Port 2: 0000.0100 power
   Port 3: 0000.0100 power
   Port 4: 0000.0507 highspeed power suspend enable connect
   Port 5: 0000.0100 power
   Port 6: 0000.0100 power
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass            9 Hub
  bDeviceSubClass         0 Unused
  bDeviceProtocol         0 Full speed (or root) hub
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0001
  Self Powered

Bus 002 Device 003: ID 064e:e285 Suyin Corp. 
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  idVendor           0x064e Suyin Corp.
  idProduct          0xe285 
  bcdDevice            0.12
  iManufacturer           1 SuYin
  iProduct                3 Integrated Camera
  iSerial                 2 HF0316-S71L-MI03-VL-R00.01.02
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength          529
    bNumInterfaces          2
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Association:
      bLength                 8
      bDescriptorType        11
      bFirstInterface         0
      bInterfaceCount         2
      bFunctionClass         14 Video
      bFunctionSubClass       3 Video Interface Collection
      bFunctionProtocol       0 
      iFunction               0 
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      1 Video Control
      bInterfaceProtocol      0 
      iInterface              0 
      VideoControl Interface Descriptor:
        bLength                13
        bDescriptorType        36
        bDescriptorSubtype      1 (HEADER)
        bcdUVC               1.00
        wTotalLength           77
        dwClockFrequency       30.000000MHz
        bInCollection           1
        baInterfaceNr( 0)       1
      VideoControl Interface Descriptor:
        bLength                18
        bDescriptorType        36
        bDescriptorSubtype      2 (INPUT_TERMINAL)
        bTerminalID             1
        wTerminalType      0x0201 Camera Sensor
        bAssocTerminal          0
        iTerminal               0 
        wObjectiveFocalLengthMin      0
        wObjectiveFocalLengthMax      0
        wOcularFocalLength            0
        bControlSize                  3
        bmControls           0x00002a0e
          Auto-Exposure Mode
          Auto-Exposure Priority
          Exposure Time (Absolute)
          Zoom (Absolute)
          PanTilt (Absolute)
          Roll (Absolute)
      VideoControl Interface Descriptor:
        bLength                26
        bDescriptorType        36
        bDescriptorSubtype      6 (EXTENSION_UNIT)
        bUnitID                 2
        guidExtensionCode         {92423946-d10c-e34a-8783-3133f9eaaa3b}
        bNumControl             3
        bNrPins                 1
        baSourceID( 0)          1
        bControlSize            1
        bmControls( 0)       0xff
        iExtension              0 
      VideoControl Interface Descriptor:
        bLength                11
        bDescriptorType        36
        bDescriptorSubtype      5 (PROCESSING_UNIT)
      Warning: Descriptor too short
        bUnitID                 3
        bSourceID               2
        wMaxMultiplier          0
        bControlSize            2
        bmControls     0x0000157f
          Brightness
          Contrast
          Hue
          Saturation
          Sharpness
          Gamma
          White Balance Temperature
          Backlight Compensation
          Power Line Frequency
          White Balance Temperature, Auto
        iProcessing             0 
        bmVideoStandards     0x 9
          None
          SECAM - 625/50
      VideoControl Interface Descriptor:
        bLength                 9
        bDescriptorType        36
        bDescriptorSubtype      3 (OUTPUT_TERMINAL)
        bTerminalID             4
        wTerminalType      0x0101 USB Streaming
        bAssocTerminal          0
        bSourceID               3
        iTerminal               0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0008  1x 8 bytes
        bInterval              16
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       0
      bNumEndpoints           0
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      VideoStreaming Interface Descriptor:
        bLength                            14
        bDescriptorType                    36
        bDescriptorSubtype                  1 (INPUT_HEADER)
        bNumFormats                         1
        wTotalLength                      341
        bEndPointAddress                  129
        bmInfo                              0
        bTerminalLink                       4
        bStillCaptureMethod                 1
        bTriggerSupport                     0
        bTriggerUsage                       0
        bControlSize                        1
        bmaControls( 0)                    27
      VideoStreaming Interface Descriptor:
        bLength                            27
        bDescriptorType                    36
        bDescriptorSubtype                  4 (FORMAT_UNCOMPRESSED)
        bFormatIndex                        1
        bNumFrameDescriptors                7
        guidFormat                            {59555932-0000-1000-8000-00aa00389b71}
        bBitsPerPixel                      16
        bDefaultFrameIndex                  1
        bAspectRatioX                       0
        bAspectRatioY                       0
        bmInterlaceFlags                 0x00
          Interlaced stream or variable: No
          Fields per frame: 2 fields
          Field 1 first: No
          Field pattern: Field 1 only
          bCopyProtect                      0
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         1
        bmCapabilities                   0x01
          Still image supported
        wWidth                            640
        wHeight                           480
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize      614400
        dwDefaultFrameInterval         363636
        bFrameIntervalType                  4
        dwFrameInterval( 0)            363636
        dwFrameInterval( 1)            363637
        dwFrameInterval( 2)            363638
        dwFrameInterval( 3)            363639
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         2
        bmCapabilities                   0x01
          Still image supported
        wWidth                           1280
        wHeight                           720
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize     1843200
        dwDefaultFrameInterval        1333332
        bFrameIntervalType                  4
        dwFrameInterval( 0)           1428571
        dwFrameInterval( 1)           1428572
        dwFrameInterval( 2)           1428573
        dwFrameInterval( 3)           1428574
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         3
        bmCapabilities                   0x01
          Still image supported
        wWidth                            352
        wHeight                           288
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize      202752
        dwDefaultFrameInterval         363636
        bFrameIntervalType                  4
        dwFrameInterval( 0)            363636
        dwFrameInterval( 1)            363637
        dwFrameInterval( 2)            363638
        dwFrameInterval( 3)            363639
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         4
        bmCapabilities                   0x01
          Still image supported
        wWidth                            320
        wHeight                           240
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize      153600
        dwDefaultFrameInterval         363636
        bFrameIntervalType                  4
        dwFrameInterval( 0)            363636
        dwFrameInterval( 1)            363637
        dwFrameInterval( 2)            363638
        dwFrameInterval( 3)            363639
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         5
        bmCapabilities                   0x01
          Still image supported
        wWidth                            176
        wHeight                           144
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize       50688
        dwDefaultFrameInterval         363636
        bFrameIntervalType                  4
        dwFrameInterval( 0)            363636
        dwFrameInterval( 1)            363637
        dwFrameInterval( 2)            363638
        dwFrameInterval( 3)            363639
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         6
        bmCapabilities                   0x01
          Still image supported
        wWidth                            160
        wHeight                           120
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize       38400
        dwDefaultFrameInterval         363636
        bFrameIntervalType                  4
        dwFrameInterval( 0)            363636
        dwFrameInterval( 1)            363637
        dwFrameInterval( 2)            363638
        dwFrameInterval( 3)            363639
      VideoStreaming Interface Descriptor:
        bLength                            42
        bDescriptorType                    36
        bDescriptorSubtype                  5 (FRAME_UNCOMPRESSED)
        bFrameIndex                         7
        bmCapabilities                   0x01
          Still image supported
        wWidth                            640
        wHeight                           360
        dwMinBitRate                   912384
        dwMaxBitRate                   912384
        dwMaxVideoFrameBufferSize      460800
        dwDefaultFrameInterval         363636
        bFrameIntervalType                  4
        dwFrameInterval( 0)            363636
        dwFrameInterval( 1)            363637
        dwFrameInterval( 2)            363638
        dwFrameInterval( 3)            363639
      VideoStreaming Interface Descriptor:
        bLength                             6
        bDescriptorType                    36
        bDescriptorSubtype                 13 (COLORFORMAT)
        bColorPrimaries                     1 (BT.709,sRGB)
        bTransferCharacteristics            1 (BT.709)
        bMatrixCoefficients                 4 (SMPTE 170M (BT.601))
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       1
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1400  3x 1024 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       2
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1340  3x 832 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       3
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x1300  3x 768 bytes
        bInterval               1
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        1
      bAlternateSetting       4
      bNumEndpoints           1
      bInterfaceClass        14 Video
      bInterfaceSubClass      2 Video Streaming
      bInterfaceProtocol      0 
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x81  EP 1 IN
        bmAttributes            5
          Transfer Type            Isochronous
          Synch Type               Asynchronous
          Usage Type               Data
        wMaxPacketSize     0x13fc  3x 1020 bytes
        bInterval               1
Device Qualifier (for other device speed):
  bLength                10
  bDescriptorType         6
  bcdUSB               2.00
  bDeviceClass          239 Miscellaneous Device
  bDeviceSubClass         2 ?
  bDeviceProtocol         1 Interface Association
  bMaxPacketSize0        64
  bNumConfigurations      1
Device Status:     0x0000
  (Bus Powered)
```

/proc/cpuinfo
```

processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 42
model name	: Intel(R) Core(TM) i3-2367M CPU @ 1.40GHz
stepping	: 7
cpu MHz		: 800.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 2793.81
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 42
model name	: Intel(R) Core(TM) i3-2367M CPU @ 1.40GHz
stepping	: 7
cpu MHz		: 800.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 0
cpu cores	: 2
apicid		: 1
initial apicid	: 1
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 2793.62
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 2
vendor_id	: GenuineIntel
cpu family	: 6
model		: 42
model name	: Intel(R) Core(TM) i3-2367M CPU @ 1.40GHz
stepping	: 7
cpu MHz		: 800.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 2
apicid		: 2
initial apicid	: 2
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 2793.66
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 3
vendor_id	: GenuineIntel
cpu family	: 6
model		: 42
model name	: Intel(R) Core(TM) i3-2367M CPU @ 1.40GHz
stepping	: 7
cpu MHz		: 800.000
cache size	: 3072 KB
physical id	: 0
siblings	: 4
core id		: 1
cpu cores	: 2
apicid		: 3
initial apicid	: 3
fpu		: yes
fpu_exception	: yes
cpuid level	: 13
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 x2apic popcnt xsave avx lahf_lm arat epb xsaveopt pln pts dts tpr_shadow vnmi flexpriority ept vpid
bogomips	: 2793.66
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:
```

---

### Post by connect404 on 2011-12-13
I've been doing some initial power usage tests, these results are fairly objective at present.. but since only owning the laptop for 2 days I am yet to get a good feel for battery usage. I have been using powerstat to generate ACPI power usage. All tests are with:
[LIST]
[*]Bluetooth soft-off
[*]wifi connected to a wifi-N AP
[*]no AC connected
[*]320gb 5400rpm HDD
[*]8gb of RAM
[/LIST]

Powerstat in the default mode will let the machine settle for 120 secs then take 30 samples over 5 mins and present the average. run from the terminal with:   'sudo powerstat'

Install powerstat with:
```
sudo add-apt-repository ppa:colin-king/powermanagement
sudo apt-get update
sudo apt-get install powerstat
```

**When run on a stock x121e idling power consumption is**
```

Summary:
 10.39 Watts on Average with Standard Deviation 0.10
```


**Stock setup with [echo SATA_ALPM_ENABLE=true | sudo tee /etc/pm/config.d/sata_alpm]("https://wiki.ubuntu.com/Kernel/PowerManagementALPM")**
```
Summary:
 10.28 Watts on Average with Standard Deviation 0.13
```


**As above with "pm-powersave true"**
```
Summary:
 10.01 Watts on Average with Standard Deviation 0.11
```


**As above with kernel option "aspm=force"**
edit /etc/default/grub (root privileges required) and change:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force"
sudo update-grub
```
Summary:
  9.19 Watts on Average with Standard Deviation 0.16
```


[B]All above disabled, then aspm=force turned on and TLP installed and setup. I recommend you [read a bit about TLP]("https://github.com/linrunner/TLP/wiki/TLP-Linux-Advanced-Power-Management").
[/B]```
sudo apt-add-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tp-smapi-dkms
```
```
Summary:
  8.61 Watts on Average with Standard Deviation 0.20
```

[B]As above [with i915 RC6 enabled]("http://www.phoronix.com/scan.php?page=news_item&px=MTAyNjE")
[/B]edit /etc/default/grub (root privileges required) and change:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=force i915.i915_enable_rc6=1"
sudo update-grub

I have noticed one random lockup since turning this on... well isn't really supported yet anyway so what can you expect :)
```
Summary:
  8.39 Watts on Average with Standard Deviation 0.14
```


At the time of writing I have got 4 hours of light duty web surfing and power manager says I have 1hr21m left @ 19% remaining. I think 5 hours of usage with the above settings is a fair estimate so far. More detailed usage reports to follow.

---

### Post by zibletop on 2011-12-30
Hi,

Thanks for your installation report. I just recieve my x121e and everything is working out of the box with 11.10. 

regards

---

### Post by Daniel R.T. Hartley on 2012-01-06
I've been running Linux Mint 11 on this since September. Generally extremely happy with it...

But a couple of weeks ago few expected issues of BIOS of motherboard/graphics have emerged causing resolution issues. xrandr commands, grub edit does not fix. Either that or it's a kernel bug.

Also, though you note the battery works fine, the x121e is quite seriously effected by the power regression issues with the currently available kernels, as many other lap tops do. More than a third of battery length is lost, and cpu temperatures rise, running at 10-15c hotter than with earlier kernels without the power regression (i.e. Linux Mint 11 and the kernel 2.6x rather than Mint 12 and the 3.x, which is going to remain that way until kernel 3.3. comes out).

The resolution issue (maybe completely unrelated to linux) is a total bummer, and the power regression issue is pretty much unacceptable.

But as a user, completely stable (with all updates).

---

### Post by zibletop on 2012-01-07
I have found a small typo in one of the previous message: it is dkms and not dkm. The corrected code is:

> **connect404 said:**
> 
```
sudo apt-add-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tp-smapi-dkms
```


---

### Post by connect404 on 2012-01-09
> **Daniel R.T. Hartley said:**
> 
The resolution issue (maybe completely unrelated to linux) is a total bummer, and the power regression issue is pretty much unacceptable.


I agree it does run a bit hotter than previous kernels, but 7 hours of usable battery life is on par with Windows7 reports.

---

### Post by connect404 on 2012-01-09
> **zibletop said:**
> I have found a small typo in one of the previous message: it is dkms and not dkm. The corrected code is:

fixed.

Also added an issue I've noticed. When returning from suspend the card reader no longer functions.

---

### Post by MorrisseyJ on 2012-02-04
Hi, 

I love this machine, but i am struggling with the graphics issues. I can put up with the odd artifact and i can deal with the icons sometimes behaving strangely in my file browser but the disappearing of lines of text while i am working in a text editor is infuriating. 

If anyone knows a fix for this, i'd be grateful.

On the power regression issues, using some of the fixes provided above i can get my battery to about 6 hours - also using Jupiter. 

Thanks,

---

### Post by MorrisseyJ on 2012-02-23
Using a Thinkpadx121e, running 11.10. 

Sometimes when i start up in Ubuntu the track point doesn't initialise. The only way that i know to fix it is to reboot and try again. Usually it works after one reboot, but its still a hassle.

I was just wondering if someone knew a permanent fix for this or if anyone knows of a terminal command or something which could force the track point to initialise.

Thanks,

j

---

### Post by connect404 on 2012-02-29
> **MorrisseyJ said:**
> Using a Thinkpadx121e, running 11.10. 

Sometimes when i start up in Ubuntu the track point doesn't initialise. The only way that i know to fix it is to reboot and try again. Usually it works after one reboot, but its still a hassle.

I was just wondering if someone knew a permanent fix for this or if anyone knows of a terminal command or something which could force the track point to initialise.

Thanks,

j

I've noticed this too on the odd occasion. Sometimes from returning from suspend too. I haven't found (or looked) for a fix yet.

---

### Post by jvermeulen on 2012-03-05
Has anyone got the UMTS (3G) module working in Ubuntu?

By the way, is the Intel version of the Lenovo x121e with Intel HD 3000 GPU better supported and more stable (through open source drivers) than the version with the AMD Fusion E-450 APU? Several reports mention that suspend/hibernate doesn't work that well with the AMD versions.

Thanks!

---

### Post by DrScholl on 2012-03-25
connect404 you're my hero ;)

On my brand new X121e with a gnome 3 ubuntu 11.10, I only got 3 to 4 hours of battery, I was even concerned being flogged a 4 cells battery instead of the 6 cells I ordered, but no.
When I first ran Powerstat I got a 15 W average.
Now after a simple "aspm=force" I get a 6.13 Watts on average with standard Deviation 0.05
And I haven't even configured TLP yet

Warm greetings from southern France  8-)

---

### Post by zibletop on 2012-05-13
> **MorrisseyJ said:**
> Using a Thinkpadx121e, running 11.10. 

Sometimes when i start up in Ubuntu the track point doesn't initialise. The only way that i know to fix it is to reboot and try again. Usually it works after one reboot, but its still a hassle.

I was just wondering if someone knew a permanent fix for this or if anyone knows of a terminal command or something which could force the track point to initialise.

Thanks,

j
I have the same issue. It happens roughly once a week. There is a bug record concerning this [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/986942")
regards

---

### Post by jienchi on 2012-05-23
With Ubuntu 12.04 are the above power issues automatically fixed? Or do I need to do some of the above fixes, and if so which ones?

And does anyone have any experience with the fingerprint reader?

I'm very new to Ubuntu so just learning my way around...

Thanks

Jienchi

---

### Post by zibletop on 2012-06-19
> **jienchi said:**
> With Ubuntu 12.04 are the above power issues automatically fixed? Or do I need to do some of the above fixes, and if so which ones?

And does anyone have any experience with the fingerprint reader?

I'm very new to Ubuntu so just learning my way around...

Thanks

Jienchi

Concerning RC6 it should be enabled by default when the 3.4 kernel will be released to ubuntu. The actual one is 3.2.0-25-generic then you have to enable RC6 manually in grub (see the firsts post of this thread for details).

See [Linux 3.4 will use Intel's power saving RC6 GPU technology - The H Open: News and Features](http://www.h-online.com/open/news/item/Linux-3-4-will-use-Intel-s-power-saving-RC6-GPU-technology-1503382.html)

or try this search [rc6 power saving linux kernel - Google](https://encrypted.google.com/search?q=rc6+power+saving+linux+kernel)

I haven't got fingerprint reader so...

regards

---

### Post by MorrisseyJ on 2012-06-26
>                      Originally Posted by **MorrisseyJ**                     [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11711705#post11711705")                 
                 [I]Using a Thinkpadx121e, running 11.10. 

Sometimes when i start up in Ubuntu the track point doesn't initialise.  The only way that i know to fix it is to reboot and try again. Usually  it works after one reboot, but its still a hassle.

I was just wondering if someone knew a permanent fix for this or if  anyone knows of a terminal command or something which could force the  track point to initialise.

Thanks,

j[/I]
Here is someone writing something intelligible about this. It does however appear beyond my ability to fix. i thought that someone here might know what to do with it.

[https://bbs.archlinux.org/viewtopic.php?pid=1117026](https://bbs.archlinux.org/viewtopic.php?pid=1117026)

j

---

### Post by jienchi on 2012-07-06
> **zibletop said:**
> Concerning RC6 it should be enabled by default when the 3.4 kernel will be released to ubuntu. The actual one is 3.2.0-25-generic then you have to enable RC6 manually in grub (see the firsts post of this thread for details).

See [Linux 3.4 will use Intel's power saving RC6 GPU technology - The H Open: News and Features]("http://www.h-online.com/open/news/item/Linux-3-4-will-use-Intel-s-power-saving-RC6-GPU-technology-1503382.html")

or try this search [rc6 power saving linux kernel - Google]("https://encrypted.google.com/search?q=rc6+power+saving+linux+kernel")

I haven't got fingerprint reader so...

regards

Thanks, so from what I can see 12.04 has RC6 enabled by default. I've done APSM=force and installed TLP, went from 8.54 W to 6.62W. Havent found anything for the fingerprint reader though.....

---

### Post by MorrisseyJ on 2013-02-01
>  	 		**Re: Lenovo x121e i3 Linux Hardware Compatability**
 		 	Quote:
 	 	 		 			 				                     Originally Posted by **MorrisseyJ**                     [[IMG]http://ubuntuforums.org/images/rebrand/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=11711705#post11711705")                 
                 [I]Using a Thinkpadx121e, running 11.10. 

Sometimes when i start up in Ubuntu the track point doesn't initialise.   The only way that i know to fix it is to reboot and try again. Usually   it works after one reboot, but its still a hassle.

I was just wondering if someone knew a permanent fix for this or if   anyone knows of a terminal command or something which could force the   track point to initialise.

Thanks,

j[/I] 			 		 	 	 
Here is someone writing something intelligible about this. It does  however appear beyond my ability to fix. i thought that someone here  might know what to do with it.

[https://bbs.archlinux.org/viewtopic.php?pid=1117026](https://bbs.archlinux.org/viewtopic.php?pid=1117026)

j 	

Here is some more on this, see post # 5: [https://bbs.archlinux.org/viewtopic.php?pid=1117026](https://bbs.archlinux.org/viewtopic.php?pid=1117026)

---

### Post by MorrisseyJ on 2013-05-21
Hi getting some problems with 13.04 on my x131e. Random system freeze leaves me unable to input or output anything. 

Is anyone else having this problem?

---

