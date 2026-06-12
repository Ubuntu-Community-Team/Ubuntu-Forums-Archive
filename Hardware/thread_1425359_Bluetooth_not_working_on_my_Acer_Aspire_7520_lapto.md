---
title: "Bluetooth not working on my Acer Aspire 7520 laptop"
date: 2010-03-09
forum: Hardware
---

### Post by Archy1987 on 2010-03-09
Hello everyone ! :)

I have Acer Aspire 7520 laptop, i installed ubuntu 9.10. When i open bluetooth window (system -preferences- bluetooth) it says that i don't have any bluetooth device on my laptop. The bluetooth device is not connected. Also, when i press bluetooth button on my laptop keyboard - guess what - nothing happens :D How to fix it ?

---

### Post by Fafler on 2010-03-09
Start by posting lsusb and lspci, so we can see what hardware you actually have.

Have you checked the BIOS for options for turning bluetooth on/off?

---

### Post by Archy1987 on 2010-03-09
> **Fafler said:**
> Start by posting lsusb and lspci, so we can see what hardware you actually have.

Have you checked the BIOS for options for turning bluetooth on/off?
what do u mean with isusb and ispci? sorry, i am not shure that i understand what u mean with that

yes, i checked BIOS - there is nothing about bluetooth

---

### Post by Archy1987 on 2010-03-10
bump

---

### Post by Fafler on 2010-03-10
Goto Applications -> Accessories ->Terminal and just type the commands. It will give you a list of PCI and USB devices present in your computer. Copy and paste the output here.

The fact is that most internal bluetooth devices are USB devices and supported by the btusb.ko module, but maybe it's an odd PCI device or maybe the vendor and device ID's are unknown by the kernel.

---

### Post by Archy1987 on 2010-03-11
archy@archy-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
02:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8400M G] (rev a1)
05:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
archy@archy-laptop:~$ 


archy@archy-laptop:~$ lsusb
Bus 001 Device 002: ID 5986:0102 Acer, Inc Crystal Eye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
archy@archy-laptop:~$

---

### Post by Archy1987 on 2010-03-12
bump

---

