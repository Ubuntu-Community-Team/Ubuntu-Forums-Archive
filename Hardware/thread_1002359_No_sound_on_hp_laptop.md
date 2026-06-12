---
title: "No sound on hp laptop"
date: 2008-12-04
forum: Hardware
---

### Post by shak541 on 2008-12-04
ok well.. so far i have a pretty flawless and nice install... exept... well.. my sound doesnt work 
lspci gives me this:
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

 can anyone please help out with this? i never thought i would ever have this problem in linux!

---

### Post by shak541 on 2008-12-05
ok.. so.. now i have this horrible distorted sound!!! and well.. my volume control does not work at all! :(

---

### Post by shak541 on 2008-12-09
ummm bump.. i have issues with the volume controls still! :(

---

### Post by cplusruss on 2008-12-10
I hate ALSA.  I wish I knew of an alternative.  *bump*  I've got the same deal.

---

### Post by Airfoot on 2008-12-10
try killing pulseaudio, it could be that it is conflicting with alsa.  
In terminal:

$ pulseaudio -k

---

### Post by Mike Beggs on 2008-12-10
I had similar sound troubles on my HP laptop also but this fixed it, thanks to ohingst in this thread: [http://ubuntuforums.org/showthread.php?t=993075](http://ubuntuforums.org/showthread.php?t=993075)

Open terminal and type:

sudo nano /etc/modprobe.d/alsa-base

Add to the bottom of this file:

options snd-hda-intel enable_msi=1

Exit and save with CTRL-X

Reboot. It worked for me. You might need to change the 'snd-hda-intel' to whatever your device is known by, but I wouldn't know about that!

---

