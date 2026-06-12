---
title: "Blank screen after Xubuntu loads"
date: 2007-05-16
forum: Hardware &amp; Laptops
---

### Post by carderne on 2007-05-16
Hey
I recently installed Xubuntu 7.04 using the Alternate install CD, and everything went fine. Was installed on a recently formatted and completely blank 8GB HDD. After installation completed, I removed the CD, rebooted, and everything seemed to be fine. GRUB loaded, and was followed by a black screen saying loading... Underneath this then came the following error:

ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI

The Xubuntu loading screen then started and everything was good. Then, just when loading was completed, and when the login screen would be expected, the screen went blank and then went to sleep, with the Computer still sounding like it was doing something.  (which it obviously was...)

The ACPI problem worried me, but I checked, and my BIOS is ACPI enabled (though it is obviously too old) but I didn't think ACPI would be anything to do with the screen going blank.

I then booted Xubuntu in recovery mode, and manually installed and loaded the Xfce desktop. The screen went blank and went to sleep again...

I'm currently thinking that this is a Graphics card problem, seeing as the Graphics card is a PCI S3 with 2MB RAM.

Does anyone have any ideas as to how to fix this pretty irritating problem? Or should I consider buying a cheap AGP card?


The following is a pretty good list of my system specs:

_CPU:_	
                     Name:		Intel Pentium III, 450 MHz
	Alias:		Katmai, A80525
	Socket:		370

_MOBO:_	
                     Name:		Gigabyte GA-6VA
	Form Factor:	Baby AT
	Chipset:	VIA UT82C693 Apollo Pro Plus
	ISA:		2
	PCI:		4
	AGP 2x:		1
	
_RAM:_	
                     Slot 1:		64 MB
	Slot 2:		128 MB

_BIOS:_	
                     Name:		Award Modular BIOS v4.51PG
	Date:		13/07/99
	ACPI:		Yes
	(C):		1987 - 1992 Phoenix Technologies Ltd

_GFX:_	
                     Name:		S3 Trio64 V+ Turbo (86c765)
	Memory:		2 MB
	Type:		SVGA

_HDD:_	
                     Name:		FUJITSU MPD3084AT
	Size:		8046 MB

_CD:_	
                     Name:		ATAPI CD-ROM
	Speed:		24x


Thanks

---

### Post by teaker1s on 2007-05-16
firstly if you get just a terminal login or blank screen
reboot
at boot grub menu (you may need escape key)
select recovery kernel
type
sudo dpkg-reconfigure xserver-xorg
follow the prompts and for a driver select "vesa" reboot and lets see if you have gui

---

### Post by carderne on 2007-05-18
OK thanks, it's all fixed now. I had to configure a bunch of other stuff so I hopefully never broke anything. I'm getting a new graphics card soon anyway, but thanks. Greatly appreciated.

---

