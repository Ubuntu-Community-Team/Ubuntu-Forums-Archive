---
title: "Ubuntu Karmic doesn't loads"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by par.android on 2009-10-31
Hi 
I've upgraded my ubuntu jaunty to karmic (64bits) and when rebooting and choosing ubuntu to load the screen goes black, neither the loader appears. I tried to load ubuntu 9.10 generic (fourth option in the grub menu) and it loads but there's no response of the mouse pad. 
Have I screwed up my ubuntu?
Could I downgrade to jaunty?
 
 
Thanks for the answers

---

### Post by lemming465 on 2009-11-01
I always like to try a live CD to see whether or not the hardware support has regressed before committing to an upgrade.  The rate of churn in the X server is a little scary, and will probably continue to be for another two years.

> I tried to load ubuntu 9.10 generic (fourth option in the grub menu) and it loads but there's no response of the mouse pad.
There are a few other reports of trackpad regressions; you are not the only victim.  I'm not sure how long it will take for that to get fixed; it could be issues in either the kernel or the X server.  It's been OK for me on a Toshiba satellite laptop, but I probably have a different trackpad driver than you.

> Could I downgrade to jaunty?
Unfortunately there is no downgrade manager to correspond to the update-manager; upgrade is a one-way trip.  You'll pretty much have to reinstall to revert to jaunty, and depending on your patience and troubleshooting skills, that might be your best option. 

If you post more details about your hardware (laptop vendor and specific model, details of video card and jaunty drivers, ...) people can offer you more specific advice.

---

### Post by Sealbhach on 2009-11-01
Try plugging in a USB mouse, if you can get hold of one. It's a workaround until there is a fix for your trackpad.

.

---

### Post by par.android on 2009-11-05
I thought about plugging a usb mouse but then discovered that that was just one problem: when trying to play a movie the system went to de users screen and never could play a video, also there wasn't no sound.
At the end I decided to backup my files,format and reinstall jaunty. I hope this kind of issues be resolved in Lucid Lynx.


HW info for anyone having the same problems as I :
SYSTEM INFORMATION
	Running Ubuntu Linux, the 5.0 release.
	GNOME: 2.26.1 (Ubuntu 2009-05-06)
	Kernel version: 2.6.28-16-generic (#55-Ubuntu SMP Tue Oct 20 19:48:32 UTC 2009)
	GCC: 4.3.3 (x86_64-linux-gnu)
	Xorg: unknown (09 April 2009  02:11:54AM) (09 April 2009  02:11:54AM)
	Hostname: miguel-laptop
	Uptime: 0 days 2 h 3 min

CPU INFORMATION
	GenuineIntel, Pentium(R) Dual-Core CPU       T4200  @ 2.00GHz
	Number of CPUs: 2
	CPU clock currently at 1200.000 MHz with 1024 KB cache
	Numbering: family(6) model(23) stepping(10)
	Bogomips: 3990.16
	Flags: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx lm constant_tsc arch_perfmon pebs bts rep_good pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm xsave lahf_lm

MEMORY INFORMATION
	Total memory: 2913 MB
	Total swap: 8534 MB

STORAGE INFORMATION
	SCSI device -  scsi0
		Vendor:  ATA      
		Model:  Hitachi HTS54503 
	SCSI device -  scsi1
		Vendor:  HL-DT-ST 
		Model:  DVDRAM GT20N     

HARDWARE INFORMATION
MOTHERBOARD
	Host bridge
		Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 09)
		Subsystem: Acer Incorporated [ALI] Device 0219
	
GRAPHIC CARD
	VGA controller
		Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09)
		Subsystem: Acer Incorporated [ALI] Device 0219

SOUND CARD
	Multimedia controller
		Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
		Subsystem: Acer Incorporated [ALI] Device 0219

NETWORK
	Network controller
		Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
		Subsystem: Lite-On Communications Inc Device 6600
	Ethernet controller
		Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
		Subsystem: Acer Incorporated [ALI] Device 0207

---

