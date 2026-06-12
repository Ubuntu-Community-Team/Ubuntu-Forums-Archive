---
title: "Wifi on HP dv6636nr"
date: 2008-05-14
forum: Hardware
---

### Post by Modred189 on 2008-05-14
Ok, so i have scoured this forum for instructions on how to get Ubuntu 8.04 to recognize and install my wireless card. I can't find it anywhere. 

Is there any way to get it done without using the command line? Or is it that hard?
How do it install it?

(PS, I am very very very new to linux...)

---

### Post by Limbic on 2008-05-14
As a fresh Linux user, I had a nightmare getting my wireless working on my HP dv2715nr mostly due to overcomplicating things.  The stickied guides above are well worth reading but as a Linux newb I ended up confusing myself.

[This guide]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") is the one that ended up helping me the most.  I just went ahead and used the NDISWrapper from the Repositories without issue, but the real problem was making sure I was using the correct driver.  Pay very close attention to the section called "Identifying Wireless Driver"; if you're getting errors that say things like "Hardware Present" but it's not using any drivers, you're most likely just using the wrong driver.

Here's [another post]("http://ubuntuforums.org/showthread.php?p=4379996") I found very helpful.

---

### Post by Modred189 on 2008-05-15
Sorry, neither worked. The first seems tobe out of date for HArdy

---

### Post by Ayuthia on 2008-05-15
Can you go into the Terminal and post the results of lspci -nn?  HP uses a few different types of wireless cards and this will help us see what you have.  If you do not have a wired connection, please look for a line that contains Network Controller or Ethernet Controller.

---

### Post by Modred189 on 2008-05-19
Here's what that command spit out:

```

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
03:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
fred@fred-UbuntuLaptop:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0547] (rev a2)
00:01.0 ISA bridge [0601]: nVidia Corporation MCP67 ISA Bridge [10de:0548] (rev a2)
00:01.1 SMBus [0c05]: nVidia Corporation MCP67 SMBus [10de:0542] (rev a2)
00:01.2 RAM memory [0500]: nVidia Corporation MCP67 Memory Controller [10de:0541] (rev a2)
00:01.3 Co-processor [0b40]: nVidia Corporation MCP67 Co-processor [10de:0543] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:02.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:04.0 USB Controller [0c03]: nVidia Corporation MCP67 OHCI USB 1.1 Controller [10de:055e] (rev a2)
00:04.1 USB Controller [0c03]: nVidia Corporation MCP67 EHCI USB 2.0 Controller [10de:055f] (rev a2)
00:06.0 IDE interface [0101]: nVidia Corporation MCP67 IDE Controller [10de:0560] (rev a1)
00:07.0 Audio device [0403]: nVidia Corporation MCP67 High Definition Audio [10de:055c] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Bridge [10de:0561] (rev a2)
00:09.0 IDE interface [0101]: nVidia Corporation MCP67 AHCI Controller [10de:0550] (rev a2)
00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP67 Ethernet [10de:054c] (rev a2)
00:0c.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:0d.0 PCI bridge [0604]: nVidia Corporation MCP67 PCI Express Bridge [10de:0563] (rev a2)
00:12.0 VGA compatible controller [0300]: nVidia Corporation GeForce 7150M [10de:0531] (rev a2)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
02:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
02:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
02:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 12)
02:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
02:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)
03:00.0 Network controller [0280]: Broadcom Corporation BCM94311MCG wlan mini-PCI [14e4:4311] (rev 02) 
```

Thanks for your willingness to help! Ubuntu community ftw

---

### Post by Modred189 on 2008-05-21
Any ideas? Anyone?

---

### Post by Modred189 on 2008-05-23
ttt

---

### Post by Yellow Pasque on 2008-05-23
Welcome to Ubuntu/Linux. Don't fear the command line; it's our friend (as is the forum search function). Observe:
[http://ubuntuforums.org/showthread.php?t=772451](http://ubuntuforums.org/showthread.php?t=772451)

---

### Post by Modred189 on 2008-05-24
> **Temüjin said:**
> Welcome to Ubuntu/Linux. Don't fear the command line; it's our friend (as is the forum search function). Observe:
[http://ubuntuforums.org/showthread.php?t=772451](http://ubuntuforums.org/showthread.php?t=772451)
Thanks! I will give this a try and see what happens. I used the search, but this didn't come up.

---

### Post by Yellow Pasque on 2008-05-25
You're welcome. The instructions might be a little confusing for a beginner. Let me clarify a couple things:
> 2 ) Add the lines

blacklist b43
blacklist b43legacy
blacklist b44

to the very end of /etc/modprobe.d/blacklist

Use the following command to do that:
```
gksudo gedit /etc/modprobe.d/blacklist
```

> and type these commands ON DIRECTORY THAT CONTAINS bcmwl5.inf

sudo ndiswrapper -i <driver>.inf
It appears the name of the file will be bcmwl5.inf if you're using the x86 version of Ubuntu, so:
```
sudo ndiswrapper -i bcmwl5.inf
```

If you have any issues, let me know.

---

