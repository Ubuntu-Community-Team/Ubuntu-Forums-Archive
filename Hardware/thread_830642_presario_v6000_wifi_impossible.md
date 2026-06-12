---
title: "presario v6000 wifi impossible"
date: 2008-06-16
forum: Hardware
---

### Post by matthekc on 2008-06-16
My sister has a v6000 it did not get wifi in vista so first I tried throwing a belkin card and driver in it.  It still didn't work so I did a Linux install tiedy to lspci shows no wlan hardware so I thought maybe the broadcom chip is burned out. put my belkin back in but no luck.  Kind of like mission impossible I dub this machine wifi impossible. Any ideas?

Linux mint 5 but I don't think that matters.

---

### Post by lswest on 2008-06-16
can you try plugging the wifi device in (belkin) and posting back the results of ```
dmesg|tail -n 15
``` so we see if there are any errors that occur.

If the broadcom chip doesn't show up and windows couldn't use it either, chances are it is dead.

---

### Post by matthekc on 2008-06-16
My sisters laptop is retarded it will mount my usb drive in one usb port but not the other except which usb port keeps changing :confused:  I needed the usb drive to copy this.

sarah@sarah-laptop ~ $ dmesg|tail -n 15
[   39.503481] eth0: no link during initialization.
[   41.850669] ppdev: user-space parallel port driver
[   42.013710] apm: BIOS not found.
[  105.918944] Marking TSC unstable due to: cpufreq changes.
[  105.928910] Time: hpet clocksource has been installed.
[  106.424667] Clocksource tsc unstable (delta = -303610175 ns)
[  106.970171] Bluetooth: Core ver 2.11
[  106.971595] NET: Registered protocol family 31
[  106.971603] Bluetooth: HCI device and connection manager initialized
[  106.971612] Bluetooth: HCI socket layer initialized
[  107.104573] Bluetooth: L2CAP ver 2.9
[  107.104582] Bluetooth: L2CAP socket layer initialized
[  107.128779] Bluetooth: RFCOMM socket layer initialized
[  107.129812] Bluetooth: RFCOMM TTY layer initialized
[  107.129819] Bluetooth: RFCOMM ver 1.8
sarah@sarah-laptop ~ $ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
sarah@sarah-laptop ~ $

---

### Post by matthekc on 2008-06-16
maybe a controller on the motherboard is going bad

---

### Post by matthekc on 2008-06-17
So my sister has noticed that if she runs the sims the vista side gets wifi occasionally.  This machine is evil I'm going to the vista forums with this crap... wish me luck.

---

