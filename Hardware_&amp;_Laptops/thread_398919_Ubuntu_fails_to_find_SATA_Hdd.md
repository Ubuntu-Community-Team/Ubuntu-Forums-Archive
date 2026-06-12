---
title: "Ubuntu fails to find SATA Hdd"
date: 2007-04-01
forum: Hardware &amp; Laptops
---

### Post by Idwal on 2007-04-01
Ubuntu Live 6.10 fails to find the Seagate SATA 320 Gb Hdd on my Medion 8818 system.
As a consequence, I cannot install either. (The distribution starts up and runs perfectly happily.) 

The system's motherboard is built for Medion by MSI (& labelled as an MS-7318 V1.1). It uses an Intel Core 2 Duo processor running at 1.86 GHz with a VIA PT890 Northbridge and a VT8251L Southbridge (I'm not sure of the significance of the final L). The VT8251 controls the SATA interface (amongst other things).

I am trying to create a dual boot system with the XP Media Center Edition which was pre-installed on the system.

I have tried other Linux distributions, both Live and installable, with the same problem of failing to find the hard drive, (e.g. I have tried SUSE 10.2 (Live & installable), Knoppix 5.1.1 & Fedora Core 6).

I presume the problem lies with the VT8251 and its identification by Linux. I have spent a fair amount of time on the web trying to find a solution, but to no avail. The closest references have been to Asus motherboards failing to find a SATA drive, but those solutions do not seem to work with this system.

Any suggestions would, therefore be greatly appreciated.

---

### Post by moulin on 2007-04-14
I have the same problem with the same computer. I am downloading 7.04 beta now to see if Ubuntu can recognize my hard drives.

---

### Post by davids45 on 2007-05-03
G'day from another perplexed Medion 8818 owner with HD-uninstallable but otherwise working Live Ubuntu & other Linux CDs.

The computer came with a pre-installed Linux multimedia set-up (while the computer is off, press a special button and watch TV etc without starting Windows XP). This may have something to do with this lock-out of other Linuxes.  My other older Medion computers, without this "feature", happily multiply boot.

The other problem source may be the Medion's SATA hard-drive and its BIOS set-up.  Apparently adding a second hard-drive and using RAID, the second hard drive can take a Linux installation (from the Unofficial Aldi-Medion  (UK) forum).  One hard drive however and by playing with the RAID options, it's either Linux or Windows but no dual or multiple boot option.

Any advice toward dual booting, without buying another hard-drive, appreciated.

---

### Post by Bergarath on 2007-06-18
Hi,

I'm a MEDION 8822 owner.

I've tried to use Gparted (liveCd or on Ubuntu 6.06) to identify the structure of my HD. My intent was to make a new partition of my disk.

Unfortunatly, Gparted cannot recognize my HD

With Ranish partition on System Rescue CD, I can see that my HD looks like this:

IDE
Capacity	320 Gb
Cylinder	65535
Head		16
Precomp		0
Landing Zone	65534
Sector		255

			File			Starting		Ending			Partition
# 	Type 	Row	Systeme Type 		Cyl 	Head 	Sect 	Cyl 	Head 	Sect 	Size [KB]

0	MBR		Master Boot Rec		0	0	1	0	0	1	0
1	Pri		unused			0	0	2	0	32	32	1,023
2	Pri	2	Windows NT NTFS		0	32	33	35,440	38	54	284,672,000
3	Pri	1	VFAT Extended LBA	35,440	38	55	38,913	37	36	27,896,832
4	  Log		Unused			35,440	39	55	35,440	71	23	992
5	  Log		Windows FAT-32		35,440	71	24	38,913	37	36	27,895,808
6	Pri		Unused			38,913	37	37	38,913	80	63	1,368
7			Unused			0	0	0	0	0	0	0

OU

			File			Starting	Number of	Ending		Partition
# 	Type 	Row	Systeme Type 		sector		sectors		sector		Size [KB]

0	MBR		Master Boot Rec		0		1		0		0
1	Pri		unused			1		2,047		2,047		1,023
2	Pri	2	Windows NT NTFS		2,048		569,344,000	569,346,047	284,672,000
3	Pri	1	VFAT Extended LBA	569,346,048	55,793,64	625,139,711	27,896,832
4	  Log		Unused			569,346,111	1,985		569,348,095	992
5	  Log		Windows FAT-32		569,348,096	55,791,616	625,139,711	27,895,808
6	Pri		Unused			625,139,712	2,736		625,142,447	1,368
7			Unused			0		0		0		0	


does have any one a suggestion to help linux recognize my HD?

Thank U

---

### Post by rdagil on 2007-06-25
I also have problems installing Ubuntu on my MD 8822. The problem is also the recognition of the SATA drive. I've heard that by changing the IDE setup in the BIOS you should be able to install ubuntu. There are three choices in the BIOS: 1) IDE (Doen't work) 2) RAID and 3) AHCI

I'm running Vista on the computer as well, and want to run a dual boot environment. I've tried to change the BIOS to AHCI, it gives BSOD in Vista, but this can be fixed in the registry. However, the hard drives are very slow when running AHCI, so this isn't optimal at all. When trying to boot as RAID Vista gives BSOD as well, and so far I havn't been able to solve this problem. I don't know if the hard drives can be "seen" by ubuntu running in RAID or AHCI.

I hope a solution will present itself!

Robert

---

### Post by MegaWatty on 2008-01-22
Have a look at this...

[http://ubuntuforums.org/showthread.php?t=609561](http://ubuntuforums.org/showthread.php?t=609561)

As short term fix set BIOS to AHCI, install Ubuntu, this should then boot via GRUB.

To boot into XP or VISTA change BIOS back to IDE & select via GRUB at start up.

Still searching for proper solution!

---

