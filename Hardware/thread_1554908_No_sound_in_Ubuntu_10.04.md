---
title: "No sound in Ubuntu 10.04"
date: 2010-08-17
forum: Hardware
---

### Post by SaswataDutta on 2010-08-17
I recently installed Ubuntu 10.04 in my Sony Vaio (VPCEB24En) laptop. Everything is working fine except there is no sound.

---

### Post by mitsios on 2010-08-17
In a terminal, type this
```
lspci
```and post the output

---

### Post by SaswataDutta on 2010-08-17
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc RV710/730
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd Device e822
03:00.1 System peripheral: Ricoh Co Ltd Device e230
03:00.4 SD Host controller: Ricoh Co Ltd Device e822
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Device 4381 (rev 11)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by Fafler on 2010-08-17
It should use the snd-hda-intel driver (lsmod to be sure) and it might be that the card is detected okay, but isn't configured the right way. Try look at this and try out some different models. [http://www.alsa-project.org/main/index.php/Help_To_Debug_Intel_HDA#.27model.27_parameter](http://www.alsa-project.org/main/index.php/Help_To_Debug_Intel_HDA#.27model.27_parameter)

---

### Post by lidex on 2010-08-17
Go here:
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by bnarenderraju on 2010-09-07
> **SaswataDutta said:**
> I recently installed Ubuntu 10.04 in my Sony Vaio (VPCEB24En) laptop. Everything is working fine except there is no sound.
 
I have the same sony vaio model laptop, but the boot menu is stuck while installing ubuntu 10.04 64-bit on core i3 win7 in Virtual box.can anyone help me how to install ....

---

