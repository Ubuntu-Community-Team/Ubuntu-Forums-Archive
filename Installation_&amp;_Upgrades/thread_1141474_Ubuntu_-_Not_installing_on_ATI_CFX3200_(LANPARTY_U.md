---
title: "Ubuntu - Not installing on ATI CFX3200 (LANPARTY UT CFX3200-DR)"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by eumoria on 2009-04-28
Let me try to explain this fully so maybe I can get some answers about this problem.

I am an Ubuntu user/lover for a long time now. My OLD system was a VIA KT800 with AGP NVIDIA card. It ran Ubuntu beautifully and everything was wonderful. My performance was lagging behind, though, so I picked up a new system (used) from a friend and these are the specs of the NEW non-Ubuntu-working system:

LANPARTY UT CFX3200-DR Motherboard
AMD Athlon 64 4000+
2gig Generic RAM
ATI Radeon X1800
PATA Hard Disk
PATA CDROM

Ever since upgrading to this system I have never been able to install Ubuntu. The install script always crashes before even loading the UI for installation. This is happening on 8.04 and now on 9.04 it is the same (even worse it crashes earlier).

I have run Debian on this machine with no problems and am currently on Windows XP (sadly) typing this with absolutely zero issues. I'm a PC technician and have run every test imaginable and there are no 'flaws' with the system memory, I/O or processor. I think the issue may be odd chipset I have.

The motherboard has;

Northbridge - ATI CrossFire CFX3200
Southbridge - ULI M1575

They only made the CFX3200 for a short while because AMD bought ATI soon after production started. I've been told that they just renamed the technology 'AMD 580X Chipset' but regardless I think it's what could possibly be causing my headaches with Ubuntu.

Has ANYONE had a similar problem with this type of setup? Are there any ways I can get Ubuntu installed on this setup?

HELP ME! :(

Thanks in advance for any assistance.

Christopher W. Askin

---

### Post by eumoria on 2009-05-04
:confused:

Anyone having anything similar??

---

### Post by pietjanjaap on 2009-05-04
Search for noacpi,no-apic, no-lapic etc. (and more).(bootoptions).
Boot with this and try the other.

Can you boot from the livecd?

Check your bios for sata/ide controller, there should be options like ide or sata, and native or ?(this last one is that the harddrive is seen without driver).

---

### Post by eumoria on 2009-05-11
No it currently doesn't boot to the LiveCD

I didn't even think of the SATA mode. As of now I'm using what the BIOS refers to as 'Emulated PATA Mode' which I would assume means exactly what it says.

I'll try to boot options along with the SATA controller options! Thank you so much!

---

### Post by watsupfool on 2009-09-03
Hi there, I am just here to inquire if this thread helped you solve the problem you experienced or if there was another reason behind the install failure. I am using the same motherboard and have tryed everything i can think of and find on the net without success. 
For more information i am using a 3700+ which is the same core, 1 stick of drr400 512mb, a misrable 80G HDD on ide and i am trying to install Ubuntu Server 9.04. If someone could help me i would be extremely happy as this is starting to give me a headache. Oh and go easy on me, i have messed about on linux distros before but i am still what you would call a little green :)

Thanx for any help posted in advance :)

---

### Post by eumoria on 2009-09-03
No, to this day I still haven't been able to install Ubuntu with this motherboard.

---

### Post by eumoria on 2009-09-03
I'm still convinced it's the chipset because of the short time it existed. People with the AMD version of this chipset (AMD 580X Chipset) seem to have no issues. The CrossFire3200 however seems to be the core of my problems.

---

### Post by steev_666 on 2009-09-30
Hi Basically i had exactly the same motherboard and configuration.

i ben test Ubuntu from 7.04 and had no problems to install, but i gess maybe your problem be usin SATA, The one from ULI Chip some times give me problems, i use the SATA From Silicon device.

My Config its:

> 00:00.0 Host bridge: ATI Technologies Inc RD580 [CrossFire Xpress 3200] Chipset Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:1a.0 PCI bridge: ALi Corporation M5249 HTT to PCI Bridge
00:1c.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:1c.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:1d.0 Audio device: ALi Corporation High Definition Audio/AC'97 Host Controller (rev 02)
00:1e.0 ISA bridge: ALi Corporation M1575 South Bridge
00:1e.1 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:1f.0 IDE interface: ALi Corporation M5229 IDE (rev c8)
00:1f.1 IDE interface: ALi Corporation ULi M5288 SATA (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc R580 [Radeon X1900 XT] (Primary)
01:00.1 Display controller: ATI Technologies Inc R580 [Radeon X1900 XT] (Secondary)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8052 PCI-E ASF Gigabit Ethernet Controller (rev 20)
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8053 PCI-E Gigabit Ethernet Controller (rev 22)
04:11.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
04:11.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
04:11.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
04:13.0 Mass storage controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
04:14.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev 80)


Try To install on an IDE HD, Its the only thing i gess u got diferent

Also Use the open Driver For Your VGA, if you try to install on any Ubuntu 9.04 The oficial diver it lossses support from ati on all x1xxx and before, now im using the 9.10 Beta and everithing goes right.

you can contactme if you wish, my english its not so good but i try to help you

---

