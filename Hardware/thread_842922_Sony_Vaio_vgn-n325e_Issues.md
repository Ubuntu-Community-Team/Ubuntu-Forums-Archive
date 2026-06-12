---
title: "Sony Vaio vgn-n325e Issues"
date: 2008-06-27
forum: Hardware
---

### Post by d_skillz on 2008-06-27
I am a new Linux user, Used to mess around the various distros, knoppix, redhat & mandrake. Using Pcs for 22 years from MSDOS & Win 3.1. I have just been using Ubuntu 8.04 Hard Herron for 2 weeks now on my Sony vaio vgn-n325e laptop and I have serious acpi problems. Machine wont shutdown without hard power-off, restarts fine, cant see battery state or ac adapter states. Please help, I have completely formatted vista, I am so impressed with the system responsiveness but need full laptop compatibility.

---

### Post by d_skillz on 2008-06-28
These are more indepth specs
Sony Vaio VGN-N325E/B or /W (Black or White)
15.4-inch widescreen display with xBrite-ECO LCD technology
Intel Pentium Core Duo T5300 @ 1.73ghz
Intel GMA 950 graphics 256MB Graphics Video RAM Memory
120gb 5400 rpm SATA hd
1gb ram
SuperMulti CD/DVD burner
2 USB Ports
1 4-pin iLink IEEE1304 Interface
802.11b/g Wireless Interface
Memory Stick Media
Secure Digital Slot
Express Card/34
VGA Output
Width 14.4 x Depth 10.5 x Height 1.2 to 1.6-inch
Weight 6.5 pounds with standard battery

---

### Post by d_skillz on 2008-07-03
Does no one have any similar problems? Can someone help...

---

### Post by phidia on 2008-07-03
There is a large thread [here]("http://ubuntuforums.org/showthread.php?t=465491&highlight=Sony+Vaio+vgn-n325e") on vaios it appears to deal with acpi issues-although how sucessfully I can't say.

---

### Post by d_skillz on 2008-07-03
I've checked, even posted to that thread, no one seems to help with my model, vgn-n325e. I am new to linux and would really appreciate help from the commmunity to rectify this problem.

---

### Post by d_skillz on 2008-07-06
I have extensively researched this question through google, this forum and other sources, I have also sought the expertise of a few individuals. I even submitted my dst file to a forum. It is evident that Sony Vaio has an ACPI mounting issue (not sure if that is the right terminology). In order to install Ubuntu I had to select the boot option install with ACPI workaround, I thought this would have just gotten me over the installation issue but it seems to have other repercussions. I can boot the recovery mode kernels fine and power down/suspend/resume etc without a hard powerdown. Whenever I do a normal kernel boot that is when I have to hard power down. I have posted to several linux forums with little results.

**Issues**
Battery/AC state
Backlight (fixed with x-backlight)
Function Keys
Power Down (Shut down) Forcibly

Anyone out there reading this thread, please help.

---

### Post by d_skillz on 2008-07-07
I have attached a dmi log

# dmidecode 2.9
SMBIOS 2.4 present.
17 structures occupying 713 bytes.
Table at 0x000DC010.

Handle 0x0000, DMI type 0, 24 bytes
BIOS Information
	Vendor: Phoenix Technologies LTD
	Version: R0100J4
	Release Date: 02/08/2007
	Address: 0xE7210
	Runtime Size: 101872 bytes
	ROM Size: 1024 kB
	Characteristics:
		PCI is supported
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
		Targeted content distribution is supported
	BIOS Revision: 10.0
	Firmware Revision: 10.0

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: Sony Corporation
	Product Name: VGN-N325E
	Version: C3LP8EJ3
	Serial Number: 28204334-3001074
	UUID: 3B230300-09AD-11DC-89A4-0013A9C9CFBF
	Wake-up Type: Power Switch
	SKU Number: N/A
	Family: N/A

Handle 0x0002, DMI type 2, 10 bytes
Base Board Information
	Manufacturer: Sony Corporation
	Product Name: VAIO
	Version: N/A
	Serial Number: N/A

Handle 0x0003, DMI type 3, 17 bytes
Chassis Information
	Manufacturer: Sony Corporation
	Type: Notebook
	Lock: Not Present
	Version: N/A
	Serial Number: N/A
	Asset Tag: N/A
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000

Handle 0x0004, DMI type 4, 35 bytes
Processor Information
	Socket Designation: N/A
	Type: Central Processor
	Family: Other
	Manufacturer: GenuineIntel
	ID: EC 06 00 00 FF FB E9 BF
	Version: Genuine Intel(R) CPU           T2080  @ 1.73GHz
	Voltage: 1.2 V
	External Clock: 133 MHz
	Max Speed: 1733 MHz
	Current Speed: 1733 MHz
	Status: Populated, Enabled
	Upgrade: None
	L1 Cache Handle: 0x0005
	L2 Cache Handle: 0x0006
	L3 Cache Handle: 0x0007
	Serial Number: N/A
	Asset Tag: N/A
	Part Number: N/A

Handle 0x0005, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L1 Cache
	Configuration: Enabled, Socketed, Level 1
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 64 KB
	Maximum Size: 64 KB
	Supported SRAM Types:
		Burst
		Pipeline Burst
		Asynchronous
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Data
	Associativity: 8-way Set-associative

Handle 0x0006, DMI type 7, 19 bytes
Cache Information
	Socket Designation: L2 Cache
	Configuration: Enabled, Socketed, Level 2
	Operational Mode: Write Back
	Location: Internal
	Installed Size: 1024 KB
	Maximum Size: 1024 KB
	Supported SRAM Types:
		Burst
		Pipeline Burst
		Asynchronous
	Installed SRAM Type: Other
	Speed: Unknown
	Error Correction Type: Single-bit ECC
	System Type: Unified
	Associativity: 4-way Set-associative

Handle 0x0007, DMI type 7, 19 bytes
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
	Installed SRAM Type: Unknown
	Speed: Unknown
	Error Correction Type: Unknown
	System Type: Unknown
	Associativity: Unknown

Handle 0x0008, DMI type 11, 5 bytes
OEM Strings
	String 1: 0000010007
	String 2: FNC-EXTBINSTCCIA0sod
	String 3: 01LB000000009f537f9393b18be3
	String 4: Reserved
	String 5: Reserved

Handle 0x0009, DMI type 16, 15 bytes
Physical Memory Array
	Location: System Board Or Motherboard
	Use: System Memory
	Error Correction Type: None
	Maximum Capacity: 2048 GB
	Error Information Handle: Not Provided
	Number Of Devices: 2

Handle 0x000A, DMI type 17, 21 bytes
Memory Device
	Array Handle: 0x0009
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: SODIMM
	Set: None
	Locator: SODIMM1
	Bank Locator: Bank 0
	Type: DDR2
	Type Detail: Unknown

Handle 0x000B, DMI type 17, 21 bytes
Memory Device
	Array Handle: 0x0009
	Error Information Handle: Not Provided
	Total Width: 64 bits
	Data Width: 64 bits
	Size: 512 MB
	Form Factor: SODIMM
	Set: None
	Locator: SODIMM2
	Bank Locator: Bank 1
	Type: DDR2
	Type Detail: Unknown

Handle 0x000C, DMI type 19, 15 bytes
Memory Array Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 1 GB
	Physical Array Handle: 0x0009
	Partition Width: 0

Handle 0x000D, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00000000000
	Ending Address: 0x0001FFFFFFF
	Range Size: 512 MB
	Physical Device Handle: 0x000A
	Memory Array Mapped Address Handle: 0x000C
	Partition Row Position: Unknown
	Interleave Position: Unknown
	Interleaved Data Depth: Unknown

Handle 0x000E, DMI type 20, 19 bytes
Memory Device Mapped Address
	Starting Address: 0x00020000000
	Ending Address: 0x0003FFFFFFF
	Range Size: 512 MB
	Physical Device Handle: 0x000B
	Memory Array Mapped Address Handle: 0x000C
	Partition Row Position: Unknown
	Interleave Position: Unknown
	Interleaved Data Depth: Unknown

Handle 0x000F, DMI type 32, 20 bytes
System Boot Information
	Status: No errors detected

Handle 0x0010, DMI type 127, 4 bytes
End Of Table

---

### Post by d_skillz on 2008-07-11
Thanks for replying what I ended up doing awhile ago is formating my hardrive re-install ubuntu without the power cord attached that seemed to fix the acpi issues. I now have a working battery and adapter reading. The only problem is if I allow the kernel to boot it get this error acpi_ec_wait timeout so I end up always having to select to recovery mode option. When editing the boot file and adding the line acpi=off it boots fine with no errors but of course I cannot see battery or adapter states. Recovery mode works i.e. or adding the same options to the main kernel but it doesn't auto load you have to keep selecting boot preferences. Any ideas?

---

### Post by L815 on 2008-07-12
Is is possible to edit your grub list to do what you need?

I have a Vaio Fz240e and have had minimal issues.

My issues:
-Can't hibernate
-Where touchpad is gets very warm very easily
-Brightness doesn't change

Other than that acpi seems to be reading batter and cpu temps just fine.

---

### Post by Toxicity999 on 2008-08-02
I just got one of these laptops, exactly the same. And figured it out the same night. I haven't had the time to seek why it works. but it seems to be tied to more robust use of Vesa (usplash) when first starting, press Esc on the grub countdown, edit the first entry, edit on the first content filled line. Remove splash and quiet from it. It should boot now.

Makign this more permanent, you can remove splash and quiet from defoptions in /boot/grub/menu.lst save that (save it using root), then run sudo update-grub

After this you'll see a ton of flying text as it boots, sparing you none of the subtleties of startup, but it will work.

---

### Post by d_skillz on 2008-08-30
I know that solution works I had figured it out some time ago. However that boot option requires you to select a startup mode each time you boot up fix X server, diagnostic etc. What I am after is a fix that allows me to boot normally without having to press anything at startup. Just push power button and walk away.

---

### Post by IntuitiveNipple on 2008-08-30
> **d_skillz said:**
> Thanks for replying what I ended up doing awhile ago is formating my hardThe only problem is if I allow the kernel to boot it get this error acpi_ec_wait timeout so I end up always having to select to recovery mode option.

I've got intimate knowledge of the code that handles this since I was working on a recent bug ([[Hardy] ACPI Embedded Controller (EC) stops boot when kernel boot 'quiet' option is enabled or AC power is connected](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/191137/comments/107)) that would hang many Sony Vaios totally at that point.

The latest kernel updates (2.6.24-20) fixes the issue I worked on and I wouldn't be surprised if it also fixed the symptom you're experiencing, since they look to be the very same bug.

What kernel version is being used?
```

uname -a

```

---

### Post by d_skillz on 2008-08-30
Linux Pheonix 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

---

### Post by afonteijn on 2008-08-30
Linux VAIO 2.6.24-19-generic #1 SMP Wed Aug 20 22:56:21 UTC 2008 i686 GNU/Linux

Exact same problem here. I'm currently using my laptop as a replacement desktop, so it works okay. But.. heck... it's a laptop!

I ran ubuntu 7.10 on it before, and I didn't have the splash problem. Never got the power management to run correctly though.

---

### Post by d_skillz on 2008-10-20
Interpid Ibex seems to fix our acpi issues I just tested the latest beta and the gui install/boot works fine out of the box. One for team ubuntu bug tracking.

---

### Post by insanelyderanged on 2008-10-23
i have the same laptop and i edited the menu.lst normal boot line with
acpi=off and it loads and everything fine i haven't had any problems but if this doesn't help you let me know

---

