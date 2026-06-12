---
title: "UEFI and locked BIOS"
date: 2021-05-31
forum: Hardware
---

### Post by hahu on 2021-05-31
hi, 

Been trying to figure this one out by myself for a few days now. 

I got a used gaming PC - Medion Erazer ENGINEER P10 a few days back. It originally came with a GeForce RTX 3060 but the owner had sold the card. 

PC was not used with Windows 10 preinstalled.

I _cannot_ get into BIOS to open it up, so I can install Ubuntu. 

Tried every F-key + others. 

Tried removing the battery from the mother board for a few minutes.  

Tried forcing the PC to restart into BIOS - no luck.  

The screen turns black, and the boot process stops, and I have to restart it by pressing the power button. 

Also tried starting Ubuntu from a usb stick, but the Live USB do not recognize any harddrive.  

I also tried resetting the Windows installation.  


Any ideas, or am I stuck with Windows 10? :(

intel core i7 10700F, 16 gb ram, M.2 SSD

---

### Post by Autodave on 2021-05-31
Press and hold the DEL key as you power on the PC.

---

### Post by oldfred on 2021-05-31
Does the manual have any info on correct way to reset UEFI?
Most will reset if coin battery removed. Some have jumper pins, or both work.

If UEFI Secure Boot on, UEFI setting to not allow USB boot (for security) and fast boot on which immediately boots system assuming no change makes it difficult to change settings. And if password also set, and cannot totally reset system, not much then you can do.

---

### Post by hk42 on 2021-06-02
With W10 if you press the shift key while clicking restart you get a useful menu that allows
you to restart in the BIOS.
Ubuntu allows it from the grub menu.

---

### Post by hahu on 2021-06-02
Seems the Medion Erazer Engineer P10 with the 10700F CPUS on this motherboard will leave you unable to get into bios.

 

1. Tried resetting the BIOS via pins on the MB.

2. Tried removing the battery on MB (for 20 mins)

3. Tried different monitors

4. Tried removing the m.2 ssd

5. Tried installing a different hdd

6. Tried different grfx cards

7. Can't find an English online manual of the motherboard

8. Tried using a live CD (USB) with Linux to diagnose, only to find that the BIOS uses Intel RST (which has to be disabled from BIOS)

9. Tried every F-key and DEL immediately after restarting - nothing.

10. Win 10 force boot to BIOS does not work. 

 

I really can't recommend buying this PC. It's OK until it's not, and you have to get into bios. Then it seems you locked out.

---

### Post by rbmorse on 2021-06-02
According to the owner's manual for the MEDION model 34832 Erazer Engineer X10: 

[https://www.libble.eu/medion-md-34832---erazer-engineer-x10/online-manual-939909]("https://www.libble.eu/medion-md-34832---erazer-engineer-x10/online-manual-939909/") (English) 

 pressing and holding the <DEL> on startup will access the EFI settings. If pressing and holding the <del> key doesn't work, restart the machine and at the first sign of activity press and release the <del> key at about 1 sec intervals.  You might have to do this 6 or 7 times before it registers.

---

### Post by hahu on 2021-06-03
Ty kindly for replying. Do it did not work. 

Seems I've messed up the model name. 

§ dmidecode | less - >

(snippets) 

BIOS Information
        Vendor: American Megatrends Inc.
        Version: 460H6W0X.106
        Release Date: 02/02/2021
        Address: 0xF0000
        Runtime Size: 64 kB
        ROM Size: 16 MB
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
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                ACPI is supported
                USB legacy is supported
                BIOS boot specification is supported
                Targeted content distribution is supported
                UEFI is supported
        BIOS Revision: 5.17


----

Base Board Information
        Manufacturer: MEDION
        Product Name: B460H6-EM
        Version: 1.0
        Serial Number: MV7110G11XXXXXX
        Asset Tag: Default string
        Features:
                Board is a hosting board
                Board is replaceable
        Location In Chassis: Default string
        Chassis Handle: 0x0003
        Type: Motherboard
        Contained Object Handles: 0
-----------

Handle 0x0003, DMI type 3, 22 bytes
Chassis Information
        Manufacturer: MEDION
        Type: Desktop
        Lock: Not Present
        Version: Default string
        Serial Number: Default string
        Asset Tag: Default string
        Boot-up State: Safe
        Power Supply State: Safe
        Thermal State: Safe
        Security Status: None
        OEM Information: 0x00000000
        Height: Unspecified
        Number Of Power Cords: 1
        Contained Elements: 0
        SKU Number: Default string
---------


ubuntu@ubuntu:~$ sudo dmidecode --type 0 
# dmidecode 3.2
Getting SMBIOS data from sysfs.
SMBIOS 3.2.0 present.

Handle 0x0000, DMI type 0, 26 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: 460H6W0X.106
	Release Date: 02/02/2021
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 16 MB
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
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		ACPI is supported
		USB legacy is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
		UEFI is supported
	BIOS Revision: 5.17
---





I find it odd that the mb doesn't allow bios to show up. 

I'm fairly unskilled in Linux, but have tried to google around to see if I can change bios setting from terminal. 

Can I read in terminal if bios settings are causing this?

H

---

### Post by him610 on 2021-06-05
Reference post #6
The manual for your system referenced in post #6, page 37, section...
> 13.3.1.  Executing the UEFI firmware configuration
You can only run the configuration program upon system startup. If the PC has already been started, shut down Windows® and restart it. &#61565; Before the PC reboots, press the Del key and hold it down until the message Entering Setup appears.

---

