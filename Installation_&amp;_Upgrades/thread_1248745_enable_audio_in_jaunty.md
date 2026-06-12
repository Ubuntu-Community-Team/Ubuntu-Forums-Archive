---
title: "enable audio in jaunty"
date: 2009-08-24
forum: Installation &amp; Upgrades
---

### Post by siddhuc on 2009-08-24
hi.. can anyone help me in installing or if it is already installed enabling audio drivers in jaunty?:KS

---

### Post by inobe on 2009-08-24
any special addon sound cards ?

have you right clicked volume icon select volume control and raised sound levels ?

do you have a sound icon?

---

### Post by siddhuc on 2009-08-24
ya.. i do have..

---

### Post by siddhuc on 2009-08-24
and i dont think i have special add on cards..

---

### Post by inobe on 2009-08-24
run

```
lspci
```

in terminal and paste back the output.

---

### Post by siddhuc on 2009-08-24
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
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:05.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:05.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:05.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:05.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

---

### Post by inobe on 2009-08-24
i will research this, it looks like a bug for hardy that has been fixed and you shouldn't have this problem in jaunty.

are you certain you have properly connected your speakers and wires and at least raised sound levels ?

btw' this is a no no [http://ubuntuforums.org/showthread.php?t=1244368&](http://ubuntuforums.org/showthread.php?t=1244368&)

it's against the forum rules to double post.

---

### Post by inobe on 2009-08-24
do this in terminal

```
aplay -l
```

paste back the output

---

### Post by siddhuc on 2009-08-25
card 0: NVidia [HDA NVidia], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: Conexant Digital Audio [Conexant Digital Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 6: Conexant HSF Modem [Conexant HSF Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by siddhuc on 2009-08-25
can u tell wat i have to do next?

---

### Post by inobe on 2009-08-25
it looks like you have audio, i don't understand what the problem could be.

check this guide [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

**read it before applying and fixes !**

---

