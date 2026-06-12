---
title: "Hardware Replacement (eSATA)"
date: 2018-10-30
forum: Hardware
---

### Post by talonzme on 2018-10-30
I have a PCIe to eSATA card that is not compatible with Ubuntu.  Any recommendations for a replacement card that is?  Current card is a [NewerTech MAXPower eSATA 4 port card]("https://www.newertech.com/products/pcieraidesata.php").  I also have a 2 port Vantec card (UGT-ST644R) which I cannot find drivers for.

---

### Post by dino99 on 2018-10-30
Not compatible ? What do you exactly mean ? Is the hardware found (lshw) and which journalctl error is logged ?
Do you mean you try using both cards together ? Are all ports used ?

About Newertech card:
Marvell 9235  Should work with kernel older than 4.4.0-38 [https://www.reddit.com/r/linuxquestions/comments/7pc75b/help_with_pcie_sata_controller_card/](https://www.reddit.com/r/linuxquestions/comments/7pc75b/help_with_pcie_sata_controller_card/)    
If more than one MAXPower 4-port eSATA 6G PCIe 2.0 Controller Card is installed in a PC, the computer will not boot. [https://www.newertech.com/products/pcieraidesata.php](https://www.newertech.com/products/pcieraidesata.php)

---

### Post by slickymaster on 2018-10-30
Thread moved to **Hardware** for a better fit

---

### Post by talonzme on 2018-10-31
It appears to be recognized at the hardware level.  Please excuse me, it has been a LONG time since I have done anything with Linux.  Upgrading server from WHS2011.  No errors given it just doesn't recognize the drives at all.  Below is the lshw and lspci results that match what the controller should be.  Only one installed.

```
*-storage UNCLAIMED
                description: RAID bus controller
                product: HighPoint Technologies, Inc.
                vendor: HighPoint Technologies, Inc.
                physical id: 0
                bus info: pci@0000:07:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: storage bus_master cap_list
                configuration: latency=0
                resources: ioport:ecd0(size=8) ioport:ecc8(size=4) ioport:ecd8(size=8) ioport:eccc(size=4) ioport:ece0(size=32) memory:df3ff000-df3ff7ff memory:df300000-df30ffff
```

```
00:00.0 Host bridge: Intel Corporation 5520 I/O Hub to ESI Port (rev 13)
00:01.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 1 (rev 13)
00:03.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 3 (rev 13)
00:04.0 PCI bridge: Intel Corporation 5520/X58 I/O Hub PCI Express Root Port 4 (rev 13)
00:05.0 PCI bridge: Intel Corporation 5520/X58 I/O Hub PCI Express Root Port 5 (rev 13)
00:06.0 PCI bridge: Intel Corporation 5520/X58 I/O Hub PCI Express Root Port 6 (rev 13)
00:07.0 PCI bridge: Intel Corporation 5520/5500/X58 I/O Hub PCI Express Root Port 7 (rev 13)
00:09.0 PCI bridge: Intel Corporation 7500/5520/5500/X58 I/O Hub PCI Express Root Port 9 (rev 13)
00:14.0 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub System Management Registers (rev 13)
00:14.1 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub GPIO and Scratch Pad Registers (rev 13)
00:14.2 PIC: Intel Corporation 7500/5520/5500/X58 I/O Hub Control Status and RAS Registers (rev 13)
00:1a.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IB (ICH9) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IB (ICH9) 2 port SATA Controller [IDE mode] (rev 02)
01:00.0 Ethernet controller: Broadcom Limited NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
01:00.1 Ethernet controller: Broadcom Limited NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
02:00.0 Ethernet controller: Broadcom Limited NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
02:00.1 Ethernet controller: Broadcom Limited NetXtreme II BCM5709 Gigabit Ethernet (rev 20)
03:00.0 SCSI storage controller: LSI Logic / Symbios Logic SAS1068E PCI-Express Fusion-MPT SAS (rev 08)
07:00.0 RAID bus controller: HighPoint Technologies, Inc. Device 0647 (rev 01)
08:03.0 VGA compatible controller: Matrox Electronics Systems Ltd. MGA G200eW WPCM450 (rev 0a)
fe:00.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 05)
fe:00.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 05)
fe:02.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 05)
fe:02.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 05)
fe:02.4 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 1 (rev 05)
fe:02.5 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 1 (rev 05)
fe:03.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 05)
fe:03.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 05)
fe:03.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller RAS Registers (rev 05)
fe:03.4 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 05)
fe:04.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 05)
fe:04.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 05)
fe:04.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 05)
fe:04.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 05)
fe:05.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 05)
fe:05.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 05)
fe:05.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 05)
fe:05.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 05)
fe:06.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 05)
fe:06.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 05)
fe:06.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 05)
fe:06.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 05)
ff:00.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture Generic Non-Core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 0 (rev 05)
ff:02.4 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Link 1 (rev 05)
ff:02.5 Host bridge: Intel Corporation Xeon 5500/Core i7 QPI Physical 1 (rev 05)
ff:03.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller (rev 05)
ff:03.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Target Address Decoder (rev 05)
ff:03.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller RAS Registers (rev 05)
ff:03.4 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Test Registers (rev 05)
ff:04.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Control Registers (rev 05)
ff:04.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Address Registers (rev 05)
ff:04.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Rank Registers (rev 05)
ff:04.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 0 Thermal Control Registers (rev 05)
ff:05.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Control Registers (rev 05)
ff:05.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Address Registers (rev 05)
ff:05.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Rank Registers (rev 05)
ff:05.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 1 Thermal Control Registers (rev 05)
ff:06.0 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Control Registers (rev 05)
ff:06.1 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Address Registers (rev 05)
ff:06.2 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Rank Registers (rev 05)
ff:06.3 Host bridge: Intel Corporation Xeon 5500/Core i7 Integrated Memory Controller Channel 2 Thermal Control Registers (rev 05)
```

---

### Post by talonzme on 2018-11-01
Thank you for the change slickymaster, I couldn't see any code tags to use.

---

### Post by talonzme on 2018-11-03
Despite the hardware seeming to show up in the lspci and lshw listings I cannot get anything to mount the arrays. The drives are both RAID 10 with NTFS (2 drives in first array, 4 in the second). These are transfers from a WHS2011 server that I am trying to convert without losing data.

---

### Post by talonzme on 2018-11-03
> **dino99 said:**
> Not compatible ? What do you exactly mean ? Is the hardware found (lshw) and which journalctl error is logged ?
Do you mean you try using both cards together ? Are all ports used ?

About Newertech card:
Marvell 9235  Should work with kernel older than 4.4.0-38 [https://www.reddit.com/r/linuxquestions/comments/7pc75b/help_with_pcie_sata_controller_card/](https://www.reddit.com/r/linuxquestions/comments/7pc75b/help_with_pcie_sata_controller_card/)    
If more than one MAXPower 4-port eSATA 6G PCIe 2.0 Controller Card is installed in a PC, the computer will not boot. [https://www.newertech.com/products/pcieraidesata.php](https://www.newertech.com/products/pcieraidesata.php)

I added the info you requested.  Have tried to find the RAID drives but no luck yet.

---

