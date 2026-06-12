---
title: "Wireless wont work after new install."
date: 2010-01-03
forum: Hardware
---

### Post by Moontini on 2010-01-03
I have been running ubuntu and xubuntu on my laptop for years.  they have worked automatically with my wireless card since 8.10 on a clean install.  I have been running 9.10 ubuntu since its release and it has been running fine.  
I recently got windows 7 from msdn, so I wiped my hard drive,
installed windows 7, 
installed xubuntu 9.10

and after the first reboot I got back on xubuntu 9.10 to download the windows drivers I need.  and my wireless will not work.  It doesn't even acknowledge that my laptop has a wireless card.  

if i plug in my linksys wireless G network adapter (which also has always worked)  it recognizes it and brings up networks, but will not connect to any of them.  

does anyone know what the problem might be?

---

### Post by donniesito on 2010-01-03
I had the same issue with a new 9.10 install. My only option was to hook my laptop to a router via ethernet. Once it finished installing all the updates, it recognized the wireless card and I was able to activate the restricted driver & now it works wonderfully.

I know this isn't the best "fix," but it's what I did to make things work.

Hope this helps, and good luck!

---

### Post by Moontini on 2010-01-03
I actually tried that, but i connected it directly to my modem.  it still would not connect when i connected directly to the modem, would connecting through a router change that?

---

### Post by donniesito on 2010-01-03
No - it shouldn't make a difference. So your computer isn't recognizing the ethernet NIC either? Hmmm

---

### Post by mkoehler on 2010-01-04
Well, modem or internal NIC?

---

### Post by Moontini on 2010-01-04
yeah... i just ifconfig and it didnt show any wlan cards.  so its obviously not recognizing that i even have one.

---

### Post by mkoehler on 2010-01-04
What do you see when you run lspci?

---

### Post by Moontini on 2010-01-04
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
00:12.0 VGA compatible controller: nVidia Corporation C67 [GeForce 7000M / nForce 610M] (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)


doesnt look like my card is there at all, its a F761us labtop, with some kind of atheros wireless card.

---

