---
title: "Having a hard time getting wireless to work =/"
date: 2007-07-25
forum: Hardware &amp; Laptops
---

### Post by kutos85 on 2007-07-25
Hi, I'm fairly new to linux. I just recently starting going to school at ITT Tech and a lot of the students recomended ubuntu. After trying it I fell in love with it. Ok back to my problem. I recently installed ubuntu studio feisty fawn on a hpdv9320 laptop duel boot. I got pretty much everything to work except wireless. I read quite a few post and I tried some of the steps. Few minutes later when I click the network icon on the taskbar I notice wireless it removed all together now =/. Any help would be greatly appreciated. When I type ispci i get the following:

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
00:05.0 VGA compatible controller: nVidia Corporation C51 PCI Express Bridge (rev a2)
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
03:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by xubu_caapn on 2007-07-25
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by kutos85 on 2007-07-25
I tried those steps and still no sucess.  Also the wireless network is missing from the network icon on the taskbar still.

---

### Post by xubu_caapn on 2007-07-26
hmm, that's weird. i actually had a linksys card with the broadcom chipset. it was either a 4306 or a 4311. i would've recommended you that but i couldn't find the package. anyway, how i got it to work, is i installed the package here: [http://ubuntu.cafuego.net/dists/feisty-cafuego/bcm43xx/](http://ubuntu.cafuego.net/dists/feisty-cafuego/bcm43xx/), rebooted, and my wireless worked.
here are directions, although i didn't follow these, i JUST installed the above package and it worked (it says something about the 4311, however i'm pretty sure that's what mine was and i didn't experience problems):
[http://ubuntuforums.org/showthread.php?t=391961](http://ubuntuforums.org/showthread.php?t=391961)

good luck, those broadcom cards can really be a pain.. if works comes to worse, replace it with an intel.

---

### Post by kutos85 on 2007-07-26
Thank you very much :) I finally got it working. I wish I would have found that link a few days ago... but everything is working great and it installed really fast. thanks again!

---

