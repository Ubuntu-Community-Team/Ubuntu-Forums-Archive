---
title: "Medion MD98300 no sound from headphone jack"
date: 2009-01-27
forum: Hardware
---

### Post by arranmc182 on 2009-01-27
My sound is working grate in Ubuntu but when i plug in headphones nothing so sound comes out the jack no patter what headphones or speakers you plug in to the jack

this is what i get when i go to the terminal and type lspci 

> 00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
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
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

so any help you guys can give would be nice

---

### Post by shazbot nanu nanu on 2009-02-03
same laptop, same problem...

any help?

---

### Post by shazbot nanu nanu on 2009-02-03
problem solved.

For people with the same computer look at: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/114053/comments/41](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/114053/comments/41)

---

### Post by arranmc182 on 2009-06-09
I have now fixed this problem \\:D/ its all down to the poor ALSA sound drivers ](*,) all you have to do is download the the OSS Sound drivers (they have a DEB) from [www.opensound.com]("http://www.opensound.com/")/, Then close all running programs that use the sound card then install the Drivers then restart. Now you need to change the devices that the sound outputs to, Go to System then Preferences then Sound and where ever you see Playback Devices set it to OSS4 - HD Audio play front also found that OSS4 - HD Audio spidif-out also works but crashes when two programs what to use sound at the same time. I just hope this helps any body out i think this is problem is down to poor ALSA Drivers for the ALC883 HD Audio Chip set thats in the Medion MD98300 but from what im told OSS drivers are much better for HD Audio card.

---

