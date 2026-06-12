---
title: "System Freeze, AMD 64"
date: 2008-08-23
forum: General Help
---

### Post by sabbathpriest on 2008-08-23
_**Thank you for reading this post**_

I am running Kubuntu 8.04 AMD64 on an Athlon 4000+ with 4Gb of RAM, two identical SATA 500 Gb HDD, two identical GeForce 8600 GT 256 Mb Graphics Cards on SLI.
I have only one problem: Sometimes, randomly as far as I can tell, the system freezes completely. The screen(s) freeze, the system becomes completely unresponsive, Ctrl+Alt+Backspace will not restart X, I cannot invoke the task manager and waiting does nothing (I've experimented waiting up to 6 hours). The only thing I can do is a hard reboot, and then the system reacts as if nothing odd has happened.
I apologize, I know that I am giving next to no information... 
I don't know how to diagnose or begin to investigate this problem, any pointers are greatly appreciated.

Here's the output of sysinfo:
SYSTEM INFORMATION
	Running Ubuntu Linux, the Ubuntu 8.04 (hardy) release.
	GNOME: 2.22.3 (Ubuntu 2008-07-09)
	Kernel version: 2.6.24-21-generic (#1 SMP Tue Aug 12 13:03:01 UTC 2008)
	GCC: 4.2.3 (x86_64-linux-gnu)
	Xorg: unknown (13 June 2008  01:10:57AM) (13 June 2008  01:10:57AM)
	Hostname: 555
	Uptime: 0 days 5 h 51 min

CPU INFORMATION
	AuthenticAMD, AMD Athlon(tm) 64 Processor 4000+
	Number of CPUs: 1
	CPU clock currently at 1000.000 MHz with 1024 KB cache
	Numbering: family(15) model(55) stepping(2)
	Bogomips: 2010.50
	Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow up rep_good pni lahf_lm

MEMORY INFORMATION
	Total memory: 3955 MB
	Total swap: 11585 MB

STORAGE INFORMATION
	SCSI device -  scsi0
		Vendor:  SONY     
		Model:  DVD RW DRU-190A  
	SCSI device -  scsi4
		Vendor:  ATA      
		Model:  ST3500320AS      
	SCSI device -  scsi5
		Vendor:  ATA      
		Model:  ST3500320AS      

HARDWARE INFORMATION
MOTHERBOARD
	Host bridge
		Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	PCI bridge(s)
		nVidia Corporation CK804 PCI Bridge (rev a2) (prog-if 01 [Subtractive decode])
		nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
		nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
		nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
		nVidia Corporation CK804 PCIE Bridge (rev a3) (prog-if 00 [Normal decode])
	USB controller(s)
		nVidia Corporation CK804 USB Controller (rev a2) (prog-if 10 [OHCI])
		nVidia Corporation CK804 USB Controller (rev a3) (prog-if 20 [EHCI])
	ISA bridge
		nVidia Corporation CK804 ISA Bridge (rev a3)
		Subsystem: ABIT Computer Corp. Unknown device 1c1b
	IDE interface
		nVidia Corporation CK804 Serial ATA Controller (rev f3) (prog-if 85 [Master SecO PriO])
		Subsystem: ABIT Computer Corp. Unknown device 1c1b

GRAPHIC CARD
	VGA controller
		nVidia Corporation GeForce 8600 GT (rev a1) (prog-if 00 [VGA controller])
		Subsystem: XFX Pine Group Inc. Unknown device 4016

SOUND CARD
	Multimedia controller
		nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
		Subsystem: ABIT Computer Corp. Unknown device 1c1b

NETWORK
	Ethernet controller
		Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
		Subsystem: Belkin F5D5000 PCI Card/Desktop Network PCI Card

NVIDIA GRAPHIC CARD INFORMATION
	Model name: GeForce 8600 GT
	Card Type: PCI-E 8x
	Video RAM: 256 MB
	GPU Frequency: 620 MHz
	Driver version: NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008

---

### Post by fedex1993 on 2008-08-23
I have actually had the same problem on on my machine.

```

SYSTEM INFORMATION
	Running Ubuntu Linux, the Ubuntu 8.04 (hardy) release.
	GNOME: 2.22.3 (Ubuntu 2008-07-09)
	Kernel version: 2.6.24-19-generic (#1 SMP Fri Jul 11 21:01:46 UTC 2008)
	GCC: 4.2.3 (x86_64-linux-gnu)
	Xorg: unknown (13 June 2008  01:10:57AM) (13 June 2008  01:10:57AM)
	Hostname: ubby
	Uptime: 0 days 13 h 16 min

CPU INFORMATION
	AuthenticAMD, AMD Athlon(tm) 64 X2 Dual Core Processor 4200+
	Number of CPUs: 2
	CPU clock currently at 2375.986 MHz with 512 KB cache
	Numbering: family(15) model(75) stepping(2)
	Bogomips: 4755.56
	Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp lm 3dnowext 3dnow rep_good pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy

MEMORY INFORMATION
	Total memory: 2013 MB
	Total swap: 9538 MB

STORAGE INFORMATION
	SCSI device -  scsi0
		Vendor:  TSSTcorp 
		Model:  CD/DVDW SH-S182D 
	SCSI device -  scsi2
		Vendor:  ATA      
		Model:  WDC WD5000AAJS-2 
	SCSI device -  scsi1
		Vendor:  Canon    
		Model:  MP610 series     

HARDWARE INFORMATION
MOTHERBOARD
	Host bridge
		Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
	PCI bridge(s)
		nVidia Corporation MCP55 PCI bridge (rev a2) (prog-if 01 [Subtractive decode])
		nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
		nVidia Corporation MCP55 PCI Express bridge (rev a2) (prog-if 00 [Normal decode])
	USB controller(s)
		nVidia Corporation MCP55 USB Controller (rev a1) (prog-if 10 [OHCI])
		nVidia Corporation MCP55 USB Controller (rev a2) (prog-if 20 [EHCI])
	ISA bridge
		nVidia Corporation MCP55 LPC Bridge (rev a2)
		Subsystem: ASUSTeK Computer Inc. Unknown device 8239
	IDE interface
		nVidia Corporation MCP55 SATA Controller (rev a2) (prog-if 85 [Master SecO PriO])
		Subsystem: ASUSTeK Computer Inc. Unknown device 8239

GRAPHIC CARD
	VGA controller
		nVidia Corporation G71 [GeForce 7950 GT] (rev a1) (prog-if 00 [VGA controller])
		Subsystem: eVga.com. Corp. Unknown device c637

SOUND CARD
	Multimedia controller
		nVidia Corporation MCP55 High Definition Audio (rev a2)
		Subsystem: ASUSTeK Computer Inc. Unknown device 81f6

NETWORK

NVIDIA GRAPHIC CARD INFORMATION
	Model name: GeForce 7950 GT
	Card Type: PCI-E 16x
	Video RAM: 512 MB
	GPU Frequency: 600 MHz
	Driver version: NVIDIA UNIX x86_64 Kernel Module  169.12  Thu Feb 14 17:51:09 PST 2008

```

---

### Post by sabbathpriest on 2008-08-23
Do we have the same Motherboard? Mine is an ABIT KN8-SLI

---

### Post by fedex1993 on 2008-08-23
mine is a asus m2n-sli deluxe

---

### Post by gatenby_jp on 2008-08-24
The Asus M2N motherboard has three bios settings under power ... the default settings are

suspend mode              auto
acpi version features ... disabled
acpi apic support     ... enabled

I have found that I need turn off the acpi apic support in order to boot with a knoppix cd ... try turning it off 
knoppix tends to report it as a bios bug.

I think if you try booting with the recovery kernel you will get a kernel panic unless you turn off acpi in the bios.

I have installed Kubuntu on three machines with M2N series motherboards and until i have turned that off have never been happy with the machine.

These are just my own observations and not necessarily definitive

---

### Post by sabbathpriest on 2008-08-24
It was suggested in the [Kubuntu forums]("http://kubuntuforums.net/forums/index.php?topic=3097002.0") to do a "[Alt + SysRq]("http://kubuntuforums.net/forums/index.php?topic=3088251.msg97610#msg97610")" followed by "r s e i u b" to reboot gracefully when these lockups happen. I tested the combination while the system was running properly and it did work as expected, but this morning the system locked up again and the suggested combination did not work, it didn't do anything at all.

---

### Post by warpuck on 2008-08-24
I also have a(abit AN52)Nvidia chipset AMD 4000 cpu & a ATI XL1800 dual head. I cant run mine in Dual channel mode, so I just run it with one stick (2Gb). 8.04 does not work period on that systemI fell back ver 7.10. 7.10 wont let the GUI to spread across two monitors or run separate desktops. I am going to try Kunbutu Intrepid beta, probably wont be tonight my girlfriend has warned she will be naked when I get off work! I wonder what she wants? If Kunbutu works I will let you know, I may also let you what she really wants too.

---

### Post by warpuck on 2008-08-24
> **warpuck said:**
> I also have a(abit AN52)Nvidia chipset AMD 4000 cpu & a ATI XL1800 dual head. I cant run mine in Dual channel mode, so I just run it with one stick (2Gb). 8.04 does not work period on that systemI fell back ver 7.10. 7.10 wont let the GUI to spread across two monitors or run separate desktops. I am going to try Kunbutu Intrepid beta, probably wont be tonight my girlfriend has warned she will be naked when I get off work! I wonder what she wants? If Kunbutu works I will let you know, I may also let you what she really wants too.

_________________________________________________________________
There is more than one way to skin a cat. Dont be surprised if the cat isn't happen happy after the second or third time. I didn't say cats were smart.

---

### Post by sabbathpriest on 2008-08-24
LMAO! :lolflag: Great reply man, good for you and the lucky lady!!

Anyway, back to the issue, the [Kubuntu Forums thread]("http://kubuntuforums.net/forums/index.php?topic=3097002.0") on the same helped me to narrow down the problem possible cause, and so far all seems to indicate it's the Motherboard. I will keep investigating and posting any progress on that thread.

Thanks and good luck tonight! :wink:

---

