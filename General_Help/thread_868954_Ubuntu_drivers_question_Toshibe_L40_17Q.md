---
title: "Ubuntu drivers question Toshibe L40 17Q"
date: 2008-07-24
forum: General Help
---

### Post by _d5 on 2008-07-24
Hi,

I bought a Toshiba Satellite L40 17Q laptop, and I had some issues with Windows.

I would like to run Ubuntu on my machine, but I was wandering if I was going to face some trouble with the instalation of the OS and especcially with the deivers, because I had a lot of trouble with the drivers (sound, wi fi, video and especially the SATA HDD), so could you please tell me, am I going to need to do something else then the usual Ubuntu Installation (I have made it a few times on my old PC).

If I wouldl be able to install it without any problems, I would like to ask you how to set the installation to run my Win installation first (without asking me) and then (if I press abutton or something) to run Ubuntu, but in the common case to run Win first. I read some things about GRUB and Lilo, but I still could not understand them.

But my major question is to know would i be able to run ubuntu without having to face the non-user-friendly side of Linux (the .
one which I am afraid of).

My machine according to Everest is:

	
[SIZE="3"][I]Partitions	
C: (NTFS)	14998 MB (5881 MB free)
D: (NTFS)	99472 MB (35093 MB free)
Total Size	111.8 GB (40.0 GB free)
	
Input	
Keyboard	HID Keyboard Device
Keyboard	Standard 101/102-Key or Microsoft Natural PS/2 Keyboard
Mouse	HID-compliant mouse
Mouse	Synaptics PS/2 Port TouchPad
	
Network	
Network Adapter	Realtek RTL8139/810x Family Fast Ethernet NIC  (89.215.96.72)
Modem	TOSHIBA Software Modem
	
Peripherals	
Printer	Microsoft Office Document Image Writer
USB1 Controller	Intel 82801HBM ICH8M - USB Universal Host Controller
USB1 Controller	Intel 82801HBM ICH8M - USB Universal Host Controller
USB1 Controller	Intel 82801HBM ICH8M - USB Universal Host Controller
USB1 Controller	Intel 82801HBM ICH8M - USB Universal Host Controller
USB1 Controller	Intel 82801HBM ICH8M - USB Universal Host Controller
USB2 Controller	Intel 82801HBM ICH8M - USB2 Enhanced Host Controller
USB2 Controller	Intel 82801HBM ICH8M - USB2 Enhanced Host Controller
USB Device	Realtek RTL8187B Wireless 802.11g 54Mbps USB 2.0 Network Adapter
USB Device	USB Composite Device
USB Device	USB Human Interface Device
USB Device	USB Human Interface Device
USB Device	USB Human Interface Device
Battery	Microsoft AC Adapter
Battery	Microsoft ACPI-Compliant Control Method Battery
	
DMI	
DMI BIOS Vendor	American Megatrends Inc.
DMI BIOS Version	V5.50
DMI System Manufacturer	TOSHIBA
DMI System Product	Satellite L40
DMI System Version	PSL4CE-00D005G3
DMI System Serial Number	28087784R
DMI System UUID	953581DC-E16E0DE4-7380001E-8CE84252
DMI Motherboard Manufacturer	TOSHIBA
DMI Motherboard Product	Satellite L40
DMI Motherboard Version	1.0
DMI Motherboard Serial Number	BSN12345678901234567
DMI Chassis Manufacturer	TOSHIBA
DMI Chassis Version	
DMI Chassis Serial Number	
DMI Chassis Asset Tag	
DMI Chassis Type	Notebook
DMI Total / Free Memory Sockets	2 / 0[/I][/SIZE]

Thank you in advance

---

### Post by Perkins on 2008-07-24
My father has a satellite, and you can get probably 95% functionality without doing anything special.  The standard installer should detect your windows installation and put both it and Ubuntu into a menu when you first power it on.  It's not quite what you want, since it will default to boot Ubuntu first, and you can choose windows if you want.  The bit you've read about grub though is probably enough for you to be able to change that if you want.  Just open the list and change the default.  

You might run into a few issues.  I have not had good luck with Toshiba onboard modems.  If you have the tablet version, screen rotation does not seem to work with the fancy window manager.  You have to settle for the one with no extra effects.  A couple of the models the pen input device does not seem to work properly, but on most of them it is fine.  Hibernation and automatic shutdown on low battery take a little work to make them reliable.  None of these are major problems, just little annoyances.  Personally I prefer dealing with them to the constant slowness and random crashes I was getting in windows.

---

