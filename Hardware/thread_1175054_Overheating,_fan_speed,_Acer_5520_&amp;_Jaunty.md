---
title: "Overheating, fan speed, Acer 5520 &amp; Jaunty"
date: 2009-05-31
forum: Hardware
---

### Post by jijin on 2009-05-31
My laptop is always running a little hot and I would like to change my fan settings so that it errors on the safer side.

After trying [this]("http://ubuntuforums.org/showthread.php?t=846480") tutorial, I found that it didn't work. I got the same result as [this]("http://ubuntuforums.org/showpost.php?p=5369090&postcount=2") person.

Does anybody have any ideas for me? It does not have to be the same way the tutorial did it.

Output of lspci

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
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
05:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
```

Output of sensors:

```
acpitz-virtual-0
Adapter: Virtual device
temp1:       +46.0°C  (crit = +100.0°C)                  

k8temp-pci-00c3
Adapter: PCI adapter
Core0 Temp:  +49.0°C                                    
Core0 Temp:  +46.0°C                                    
Core1 Temp:  +48.0°C                                    
Core1 Temp:  +49.0°C
```

It's really cool right now but I got the CPU Frequency Scaling Monitor applet going and I'm under only the load of Firefox and compiz. I run Urban Terror or another 3D game it gets so hot (82°C+) it causes errors, which I don't want to happen anymore.

Thanks much in advance.

---

### Post by coffeeaddict22 on 2009-05-31
Hi,
Can't comment much myself, but have a look [here]("http://ubuntuforums.org/showthread.php?t=1036051&page=6") as it looks like it's not an uncommon issue and the people there seem to be on to it.

---

### Post by jijin on 2009-06-05
Bump. Nothing in the thread above helps.. also this might be a clue :shrug: I dunno...

There is nothing in the /proc/acpi/fan/ directory. Using root terminal or sudo nautilus (making sure to show hidden files)

Anybody have any thoughts?

---

### Post by abhiroopb on 2009-06-05
I have collated all the various posts regarding this overheating issue into one ubuntuforums post...please help advise there...

[http://ubuntuforums.org/showthread.php?p=7399158#post7399158](http://ubuntuforums.org/showthread.php?p=7399158#post7399158)

Also I did not find anything in the fan directory either.

---

### Post by biscuithead1224 on 2009-07-08
I am having the same problem with my acer aspire 5000.
I found that on the intake to the fan there is a clear plastic film covering 80% of the intake. I took the cover off and took off this film and mine runs cooler than before. Hope this works for you

---

### Post by ideathproof on 2009-07-13
Well I know your trying to figure out how to mod the fan speeds, but trust me I have a 5520 and over heating is normal after a a couple of years, pull off the fan and check out the grill you will soon realise why it is over heating and I do mean **take** the fan out don't just pull the cover off and have a look because it will look clean.

---

