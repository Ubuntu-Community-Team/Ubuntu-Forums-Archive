---
title: "jaunty 9.04 Intel Drivers Problem"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by tarun86 on 2009-06-18
Hi 

I upgraded from a very stable and satisfying Hardy to Jaunty. Now the thing is this thing is a complete mess. Its installed pulseaudio which wasnt working and messed up my sound. It has some messy video drivers for intel card and so none of videos work w/o being lagged out and out of sync to death. 


I have tried everything, from getting the new patched drivers to some of the posts suggesting how to correct the xorg.conf. It dint work for me. 

This is the output of **lspci** for me
> 
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:03.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)
01:08.0 Ethernet controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) integrated LAN Controller (rev 02)

Xorg.conf that I am using at the moment. 
> Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection


[I]
If anyone has a similar chipset and has got it working with Jaunty please share your xorg.conf and other information of what you did. Please. I dont want to re-install and have wasted enough time since upgrading to Jaunty that I for once want to get it working. Please help [/I]

Thanks

---

### Post by cariboo on 2009-06-18
Have you had a look at this [thread=1130582]thread[/thread]?

---

### Post by tarun86 on 2009-06-20
Finally got it working. Anyone having chipset similar to mine, you ll find this settings helpful.

 #       Option		"AccelMethod"			"uxa"
This always crashes my X, so commented. Video are working fine now w/o lag. 

> Section "Device"
	Identifier	"Configured Video Device"
#--comment this out	
#       Option		"AccelMethod"			"uxa"
        driver          "intel"
	Option		"EXAOptimizeMigration"		"true"
	Option		"MigrationHeuristic"		"greedy"
	Option		"Tiling"			"false" 
EndSection

---

