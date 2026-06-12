---
title: "Wireless driver not detected????"
date: 2011-11-08
forum: Hardware
---

### Post by ShinigamiH4ck3r on 2011-11-08
so i just installed ubuntu 11.10 on this laptop i fixed up, and i cant get the wireless working. after hours of googleing and reading, i come to the conclusion that the brodcom sta drivers are messed up somehow because, if im right, below shows that no drivers are installed when i know that i went to additional hardware and enabled the sta drivers
[IMG]http://i640.photobucket.com/albums/uu128/anthonypage93/Screenshotat2011-11-08023953.png[/IMG]tthe above shows that its a driver problem right? if so, what the hell do i do? and if not.......what the hell do i do to get wireless working

---

### Post by crazy bird on 2011-11-08
What do you get when you type this command in a terminal: > lspci
Please paste the output here.

---

### Post by ShinigamiH4ck3r on 2011-11-08
here you are
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
00:05.0 VGA compatible controller: nVidia Corporation C51 [GeForce Go 6150] (rev a2)
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
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by TBABill on 2011-11-08
```
sudo apt-get install firmware-b43-installer b43-fwcutter
```
Edit: STA driver will not work with the BCM4311 in 11.04 and 11.10. The b43 installation step is above.

---

### Post by IcarusR on 2011-11-08
Have you tried the b43 driver ? Instructions on this page for 11.04, don't know if it will work for 11.10 but worth a try.
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04]("https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04")

---

### Post by crazy bird on 2011-11-09
This might help you also: [http://www.google.nl/search?q=broadcom+bcm4311+ubuntu+11.04&hl=nl&num=10&lr=&ft=i&cr=&safe=images&oq=broadcom+BCM4311+&aq=3&aqi=g4&aql=&gs_sm=e&gs_upl=114799l118002l0l119814l11l10l0l2l2l0l281l1047l1.5.1l7l0](http://www.google.nl/search?q=broadcom+bcm4311+ubuntu+11.04&hl=nl&num=10&lr=&ft=i&cr=&safe=images&oq=broadcom+BCM4311+&aq=3&aqi=g4&aql=&gs_sm=e&gs_upl=114799l118002l0l119814l11l10l0l2l2l0l281l1047l1.5.1l7l0)

---

### Post by ShinigamiH4ck3r on 2011-11-09
thanks people. got it working. i had to follow the [https://help.ubuntu.com/community/Wi...11_Natty_11.04](https://help.ubuntu.com/community/Wi...11_Natty_11.04) tutorial

---

