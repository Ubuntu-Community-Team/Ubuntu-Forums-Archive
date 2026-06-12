---
title: "Graphics Card"
date: 2012-01-17
forum: Hardware
---

### Post by bigtel on 2012-01-17
I have an ATI graphics card but I am having difficulty installing the driver for it - is there a terminal command which will tell me exactly what graphics card I have installed?

Thanks.

---

### Post by carl4926 on 2012-01-17
This should give you info on all your hardware and drivers currently in use

```
lspci -nnk
```

---

### Post by Mark Phelps on 2012-01-17
That command produces LOTS of output ... the line containing "VGA" is the one that will tell you the make and model video card/chipset.

That is the info we are interested in seeing.

---

### Post by bigtel on 2012-01-17
Yes - I am trying to download the correct Linux driver from the ATI website and it needs the make / model number in order to point to the right download.

Thanks for your help.

---

### Post by MoreOrLess on 2012-01-17
Run this command and post the output:
```
lspci | grep VGA
```

---

### Post by Mark Phelps on 2012-01-17
> **bigtel said:**
> Yes - I am trying to download the correct Linux driver from the ATI website and it needs the make / model number in order to point to the right download.

Thanks for your help.

Don't download the driver from there -- yet.  Please provide the "lspci" command results we asked for, first. If you force the installation of the wrong drivers, you will trash your display and then have a LOT of cleanup work to do.

---

### Post by bigtel on 2012-01-18
This is my output from lspci -nnk

```
terry@terry-A7N8X-E:~$ lspci -nnk
00:00.0 Host bridge [0600]: nVidia Corporation nForce2 IGP2 [10de:01e0] 
(rev c1)
     Subsystem: ASUSTeK Computer Inc. Device [1043:80ac]
     Kernel driver in use: agpgart-nvidia
00:00.1 RAM memory [0500]: nVidia Corporation nForce2 Memory Controller 
1 [10de:01eb] (rev c1)
     Subsystem: ASUSTeK Computer Inc. Device [1043:80ac]
00:00.2 RAM memory [0500]: nVidia Corporation nForce2 Memory Controller 
4 [10de:01ee] (rev c1)
     Subsystem: ASUSTeK Computer Inc. Device [1043:80ac]
00:00.3 RAM memory [0500]: nVidia Corporation nForce2 Memory Controller 
3 [10de:01ed] (rev c1)
     Subsystem: ASUSTeK Computer Inc. Device [1043:80ac]
00:00.4 RAM memory [0500]: nVidia Corporation nForce2 Memory Controller 
2 [10de:01ec] (rev c1)
     Subsystem: ASUSTeK Computer Inc. Device [1043:80ac]
00:00.5 RAM memory [0500]: nVidia Corporation nForce2 Memory Controller 
5 [10de:01ef] (rev c1)
     Subsystem: ASUSTeK Computer Inc. Device [1043:80ac]
00:01.0 ISA bridge [0601]: nVidia Corporation nForce2 ISA Bridge 
[10de:0060] (rev a4)
     Subsystem: ASUSTeK Computer Inc. A7N8X Mainboard [1043:80ad]
00:01.1 SMBus [0c05]: nVidia Corporation nForce2 SMBus (MCP) [10de:0064] 
(rev a2)
     Subsystem: ASUSTeK Computer Inc. Device [1043:0c11]
     Kernel driver in use: nForce2_smbus
     Kernel modules: i2c-nforce2
00:02.0 USB Controller [0c03]: nVidia Corporation nForce2 USB Controller 
[10de:0067] (rev a4)
     Subsystem: ASUSTeK Computer Inc. A7N8X Mainboard [1043:0c11]
     Kernel driver in use: ohci_hcd
00:02.1 USB Controller [0c03]: nVidia Corporation nForce2 USB Controller 
[10de:0067] (rev a4)
     Subsystem: ASUSTeK Computer Inc. A7N8X Mainboard [1043:0c11]
     Kernel driver in use: ohci_hcd
00:02.2 USB Controller [0c03]: nVidia Corporation nForce2 USB Controller 
[10de:0068] (rev a4)
     Subsystem: ASUSTeK Computer Inc. A7N8X Mainboard [1043:0c11]
     Kernel driver in use: ehci_hcd
00:04.0 Ethernet controller [0200]: nVidia Corporation nForce2 Ethernet 
Controller [10de:0066] (rev a1)
     Subsystem: ASUSTeK Computer Inc. A7N8X Mainboard onboard nForce2 
Ethernet [1043:80a7]
     Kernel driver in use: forcedeth
     Kernel modules: forcedeth
00:05.0 Multimedia audio controller [0401]: nVidia Corporation nForce 
Audio Processing Unit [10de:006b] (rev a2)
     Subsystem: ASUSTeK Computer Inc. Device [1043:0c11]
00:06.0 Multimedia audio controller [0401]: nVidia Corporation nForce2 
AC97 Audio Controler (MCP) [10de:006a] (rev a1)
     Subsystem: ASUSTeK Computer Inc. nForce2 AC97 Audio Controler (MCP) 
[1043:8095]
     Kernel driver in use: Intel ICH
     Kernel modules: snd-intel8x0
00:08.0 PCI bridge [0604]: nVidia Corporation nForce2 External PCI 
Bridge [10de:006c] (rev a3)
     Kernel modules: shpchp
00:09.0 IDE interface [0101]: nVidia Corporation nForce2 IDE [10de:0065] 
(rev a2)
     Subsystem: ASUSTeK Computer Inc. Device [1043:0c11]
     Kernel driver in use: pata_amd
     Kernel modules: pata_amd
00:0d.0 FireWire (IEEE 1394) [0c00]: nVidia Corporation nForce2 FireWire 
(IEEE 1394) Controller [10de:006e] (rev a3)
     Subsystem: ASUSTeK Computer Inc. Device [1043:809a]
     Kernel driver in use: firewire_ohci
     Kernel modules: firewire-ohci
00:1e.0 PCI bridge [0604]: nVidia Corporation nForce2 AGP [10de:01e8] 
(rev c1)
     Kernel modules: shpchp
01:04.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 
88E8001 Gigabit Ethernet Controller [11ab:4320] (rev 13)
     Subsystem: ASUSTeK Computer Inc. Marvell 88E8001 Gigabit Ethernet 
Controller (Asus) [1043:811a]
     Kernel driver in use: skge
     Kernel modules: skge
01:07.0 FireWire (IEEE 1394) [0c00]: VIA Technologies, Inc. VT6306/7/8 
[Fire II(M)] IEEE 1394 OHCI Controller [1106:3044] (rev 46)
     Subsystem: VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 
OHCI Controller [1106:3044]
     Kernel driver in use: firewire_ohci
     Kernel modules: firewire-ohci
01:08.0 Communication controller [0780]: Intel Corporation 536EP Data 
Fax Modem [8086:1040]
     Subsystem: Intel Corporation Device [8086:1000]
01:09.0 Network controller [0280]: Broadcom Corporation BCM4306 
802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
     Subsystem: Belkin F5D7000 v1000 Wireless G Desktop Card [1799:7000]
     Kernel driver in use: b43-pci-bridge
     Kernel modules: ssb
01:0b.0 RAID bus controller [0104]: Silicon Image, Inc. SiI 3112 
[SATALink/SATARaid] Serial ATA Controller [1095:3112] (rev 02)
     Subsystem: Silicon Image, Inc. SiI 3112 SATARaid Controller [1095:6112]
     Kernel driver in use: sata_sil
     Kernel modules: sata_sil
03:00.0 VGA compatible controller [0300]: ATI Technologies Inc R350 AH 
[Radeon 9800] [1002:4148]
     Subsystem: ATI Technologies Inc Device [1002:4f72]
     Kernel driver in use: radeon
     Kernel modules: radeon, radeonfb
03:00.1 Display controller [0380]: ATI Technologies Inc Radeon R350 
[Radeon 9800] (Secondary) [1002:4168]
     Subsystem: ATI Technologies Inc Device [1002:4f73]
```

---

### Post by Mark Phelps on 2012-01-18
The line containing "VGA" in the command output identifies your card as a Radeon 9800 -- for which there are no current Linux drivers from ATI.

Compatible open-source drivers for that card are installed by default.  So basically, there are no additional drivers for you to install.

ATI (now AMD) dropped Linux driver support for that card years ago, so any drivers you download from them will NOT work with that card.

---

### Post by bigtel on 2012-01-18
..so your advice would be to leave well alone..?

---

### Post by MoreOrLess on 2012-01-18
> **bigtel said:**
> ..so your advice would be to leave well alone..?
Yes!

---

