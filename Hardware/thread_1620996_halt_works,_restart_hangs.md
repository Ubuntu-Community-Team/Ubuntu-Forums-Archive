---
title: "halt works, restart hangs"
date: 2010-11-13
forum: Hardware
---

### Post by robwicks on 2010-11-13
I have a homebuilt system with Maverick 64bit on an ECS NForce4M-A v3.0 board running the latest BIOS (1.4Q). Reboots fail, stopping at the point where the screen output indicates the system is restarting. Halt, however, does power off the system. I have not modified my kernel parameters from the default. Here is dmidecode: 

# dmidecode 2.9
SMBIOS 2.2 present.
41 structures occupying 1563 bytes.
Table at 0x000F0000.

Handle 0x0000, DMI type 0, 19 bytes
BIOS Information
	Vendor: Phoenix Technologies, LTD
	Version: 6.00 PG
	Release Date: 05/26/2008
	Address: 0xE0000
	Runtime Size: 128 kB
	ROM Size: 512 kB
	Characteristics:
		ISA is supported
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
		LS-120 boot is supported
		ATAPI Zip drive boot is supported

Handle 0x0001, DMI type 1, 25 bytes
System Information
	Manufacturer:  
	Product Name:  
	Version:  
	Serial Number:  
	UUID: Not Present
	Wake-up Type: Power Switch

Handle 0x0002, DMI type 188, 255 bytes
OEM-specific Type
	Header and Data:
		BC FF 02 00 4B 38 4E 50 54 44 52 41 4D 30 03 00
		00 00 00 00 BF 00 00 00 00 00 01 00 00 00 00 00
		00 00 02 00 00 00 00 00 00 00 03 00 00 00 00 00
		00 00 04 00 00 00 00 00 00 00 05 00 00 00 00 00
		00 00 06 00 00 00 00 00 00 00 07 00 00 00 00 00
		00 00 40 00 10 0A 00 00 00 00 00 00 05 00 FB 02
		00 5D 01 00 40 00 01 00 60 00 01 00 00 00 00 00
		00 00 01 00 80 00 01 00 A0 00 00 00 00 00 00 00
		00 00 E0 3F 18 00 E0 3F 38 00 E0 3F 18 00 00 00
		00 00 46 00 00 00 00 00 00 00 52 02 00 00 00 00
		00 00 13 91 16 0C 20 12 12 05 10 00 01 00 69 00
		10 34 88 88 FF FE 15 17 17 18 16 17 16 16 15 00
		00 00 18 18 18 17 18 18 17 18 18 00 00 00 35 38
		35 38 16 16 16 16 16 16 15 16 16 18 17 18 17 17
		17 18 1A 18 38 00 38 00 22 13 11 10 00 2F 37 00
		22 12 11 20 00 2F 2B 00 00 00 00 00 00 00 00
	Strings:
		 
		 
		 
		 
		 

Handle 0x0000, DMI type 0, 192 bytes
BIOS Information
	Vendor: Not Specified
	Version: Not Specified
	Release Date: Not Specified
	ROM Size: 64 kB
	Characteristics:
	BIOS Revision: 0.0

Invalid entry length (0). DMI table is broken! Stop.


Here is lspci:00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a4)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev f1)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a4)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f3)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev f2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev f3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev f3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:06.0 Ethernet controller: Lite-On Communications Inc LNE100TX (rev 21)
01:07.0 Mass storage controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)
01:08.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 SE/7200 GS] (rev a1)

Here is lsusb:
Bus 002 Device 002: ID 0d3d:0001 Tangtop Technology Co., Ltd HID Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 4855:4288 Memorex 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

The CPU is an Athlon 64 X2 4200+

uname-a shows:
Linux nforce 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:32:27 UTC 2010 x86_64 GNU/Linux

I had issues with the forcedeth driver, so I installed a tulip card to go along with the gigabit card I have connected to another network.

Has anyone encountered this sort of issue? Also, is there anything I can do to get more information from dmidecode?

---

### Post by robwicks on 2010-11-18
I reinstalled Ubuntu. Dmidecode started out working but now has stopped. Here is the biosdecode output and the current kernel. I still cannot restart, but I can successfully halt, and the server boots fine:

# biosdecode 2.9
ACPI 1.0 present.
	OEM Identifier: Nvidia
	RSD Table 32-bit Address: 0xBFFF3040
BIOS32 Service Directory present.
	Revision: 0
	Calling Interface Address: 0x000FA820
PNP BIOS 1.0 present.
	Event Notification: Not Supported
	Real Mode 16-bit Code Address: F000:B498
	Real Mode 16-bit Data Address: F000:0000
	16-bit Protected Mode Code Address: 0x000FB470
	16-bit Protected Mode Data Address: 0x000F0000
root@nforce:/tmp/dmidecode-2.10# uname -a
Linux nforce 2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:45:36 UTC 2010 x86_64 GNU/Linux

Here is my kernel command line:

Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.35-22-generic root=UUID=14d23bf1-3433-413f-be1b-c6a4bf44746a ro verbose acpi=on hpet=force irqpoll

---

