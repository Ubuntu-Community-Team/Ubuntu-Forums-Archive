---
title: "How do I get my built-in mic &amp; cam too work???"
date: 2008-05-29
forum: Hardware
---

### Post by new2linux2008 on 2008-05-29
My laptop is a HP dv9727cl. I'm running Ubuntu 8.04 - the Hardy Heron. I have a built-in webcam and mic, but they are currently non-functional.

---

### Post by new2linux2008 on 2008-05-30
** lspci =** 
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
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by new2linux2008 on 2008-05-30
**lsusb =**
Bus 004 Device 002: ID 04f2:b023 Chicony Electronics Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000

---

### Post by new2linux2008 on 2008-05-30
got my cam to work using this tutorial:
[http://linux-uvc.berlios.de/](http://linux-uvc.berlios.de/)

---

### Post by new2linux2008 on 2008-05-30
fallowed this tutorial but my sound still is NOT working

link:
[http://10xforce.blogspot.com/2007/06/ubuntu-microphone-problems-and.html](http://10xforce.blogspot.com/2007/06/ubuntu-microphone-problems-and.html)

---

### Post by new2linux2008 on 2008-05-30
also tried 

sudo /etc/init.d/alsa-utils restart

didn't work. i'm only posting what didn't work. b/c it may work for others.

---

### Post by stchman on 2008-05-30
In gnome-sound-manager you need to enable the front mic.  I needed to do this and give the front mic a good boost for it to work.

Also are you using Cheese to run the webcam?

---

### Post by new2linux2008 on 2008-06-02
looks like my cam worked from the initial install. Mic still not working. I made sure my mic vol is up, but don't see a mic boost option anywhere

---

### Post by new2linux2008 on 2008-06-02
**lspci -v =**
 
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
	Subsystem: Hewlett-Packard Company Unknown device 30cf
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 20
	Memory at f6480000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

---

### Post by hotweiss on 2008-06-02
To get my mic working I had to do this:

A) Righ-click on the speaker in the task bar and select Open Volume Control.

B) Select Edit from the menu, and then select Preferences.

C) Click on the boxes besides Capture and Capture 1.

D) Now your microphone should be working.

---

### Post by new2linux2008 on 2008-06-02
there isn't a capture option. I did select to show my mic vol. and such and it's show it there in the vol control and is turned up. Also my sounds is working fine just my Mic isn't working. and neither is my external port for a mic, just tested that too.

---

