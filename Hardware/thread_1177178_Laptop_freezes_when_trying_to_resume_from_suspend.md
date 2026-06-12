---
title: "Laptop freezes when trying to resume from suspend"
date: 2009-06-03
forum: Hardware
---

### Post by rogier.de.groot on 2009-06-03
I have a Compaq Presario V6640ED laptop; nVidia MCP67 chipset, nVidia GeForce 7150M video card, Broadcom BCM4311 wifi-card. I'm currently using the nvidia binary driver from the repos (version 180). The laptop boots with kernel parameter "acpi=noirq". It's running Jaunty, amd64 version.

Unfortunately it won't resume after suspending it. It just freezes and I have to power down and reboot. Hibernate does work though. I've tried using uswsusp without success.

---

### Post by rogier.de.groot on 2009-06-04
Here's the output of lspci, maybe it helps:

> 00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
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
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)


---

### Post by anjo_ed on 2009-06-04
When freezes, do you can acess the terminal ( with ctrl + alt + F1 ) ?



P.S.: Tell me if my english is bad.

---

### Post by rogier.de.groot on 2009-06-04
No, it doesn't seem to be responding to keyboard input at all. The caps lock & num lock lights don't go on and off either.

---

### Post by rogier.de.groot on 2009-06-08
Bump?

---

### Post by rogier.de.groot on 2009-06-20
Anyone? I've tried every possible solution I could find; no joy so far. Vista suspends/resumes just fine on this laptop.

---

### Post by Nathan Dial on 2009-06-21
I don't know, but I'm having similar problems on my toshiba laptop.  I don't mind digging around in the issue myself, but all the reference material on debugging hibernation on laptops is from 2007 or so. (Around then, everybody started bragging about how it "just works" in Dapper--maybe I should just downgrade to dapper or 8.04 LTS or something??)

Has anyone made any other starts at a current hibernation troubleshooting guide?

---

### Post by bhadotia on 2009-06-21
> **Nathan Dial said:**
> I don't know, but I'm having similar problems on my toshiba laptop.  I don't mind digging around in the issue myself, but all the reference material on debugging hibernation on laptops is from 2007 or so. (Around then, everybody started bragging about how it "just works" in Dapper--maybe I should just downgrade to dapper or 8.04 LTS or something??)

Has anyone made any other starts at a current hibernation troubleshooting guide?

> **rogier.de.groot said:**
> I have a Compaq Presario V6640ED laptop; nVidia MCP67 chipset, nVidia GeForce 7150M video card, Broadcom BCM4311 wifi-card. I'm currently using the nvidia binary driver from the repos (version 180). The laptop boots with kernel parameter "acpi=noirq". It's running Jaunty, amd64 version.

Unfortunately it won't resume after suspending it. It just freezes and I have to power down and reboot. Hibernate does work though. I've tried using uswsusp without success.

This is what I found: [http://kdsoo.com/1286]("http://kdsoo.com/1286")

---

### Post by meditatingfrog on 2009-08-02
I just noticed the same problem resuming from suspend.  I have a Toshiba U305-S7448 laptop.  For what it's worth, here is my lspci output.  

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 01)
04:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
0a:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
0a:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
0a:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
0a:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

I'm not sure if it's related in any way, shape, or form, but I did attempt to install Firefox 3.5 (and failed).  There is a mildly annoying popup window that comes up looking for the 3.5 installation directory (which I deleted).  I'm thinking I should've stuck with 8.04.  I'll probably stick with official releases from now on.

---

### Post by 67GTA on 2009-08-02
I would start here: [http://ubuntuforums.org/showthread.php?t=1036051](http://ubuntuforums.org/showthread.php?t=1036051) You shouldn't have to boot with acpi off. Follow the first half of the how to and see what errors you have. If it is the DSDT, I can fix it.

---

