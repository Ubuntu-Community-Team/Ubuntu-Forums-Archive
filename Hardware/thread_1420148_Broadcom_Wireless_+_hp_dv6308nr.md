---
title: "Broadcom Wireless + hp dv6308nr"
date: 2010-03-02
forum: Hardware
---

### Post by six30two on 2010-03-02
Okay. I'm sick and tired of this.

Earlier I had my drivers working fine, with a good wireless connection and everything. Turned off the computer, turned it back on, no longer finding wireless drivers.

Can someone please tell me how to find the Broadcom drivers for the wireless card in a HP Pavilion dv6308nr? Please?

Been googling and searching for this answer for hours, tried a million different things, nothing is working. I need a definitive answer.

---

### Post by six30two on 2010-03-02
The card itself is a BCM94311 MCG.

---

### Post by Ayuthia on 2010-03-02
Which Broadcom driver are you using (Broadcom STA or b43)?  Can you also post the results of:
```

lshw -C network
lspci -nn

```

It will help us see which driver your card is trying to use and also let us know if there are any possible driver conflicts.

---

### Post by six30two on 2010-03-02
I'm not sure what driver I'm using now. I was using the STA drivers I could find through the Synaptic Package Manager, but then I deleted those, rebooted, and used ndisgtk to install Broadcom proprietary drivers. Only problem is that it says no matching hardware is installed. But it is, I know it is and I just double checked it.

Below are the outputs.

USER@WORKSTATION:~$ sudo lshw -C network
  *-network DISABLED      
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

USER@WORKSTATION:~$ lspci -nn
00:00.0 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02f0] (rev a2)
00:00.1 RAM memory [0500]: nVidia Corporation C51 Memory Controller 0 [10de:02fa] (rev a2)
00:00.2 RAM memory [0500]: nVidia Corporation C51 Memory Controller 1 [10de:02fe] (rev a2)
00:00.3 RAM memory [0500]: nVidia Corporation C51 Memory Controller 5 [10de:02f8] (rev a2)
00:00.4 RAM memory [0500]: nVidia Corporation C51 Memory Controller 4 [10de:02f9] (rev a2)
00:00.5 RAM memory [0500]: nVidia Corporation C51 Host Bridge [10de:02ff] (rev a2)
00:00.6 RAM memory [0500]: nVidia Corporation C51 Memory Controller 3 [10de:027f] (rev a2)
00:00.7 RAM memory [0500]: nVidia Corporation C51 Memory Controller 2 [10de:027e] (rev a2)
00:02.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fc] (rev a1)
00:03.0 PCI bridge [0604]: nVidia Corporation C51 PCI Express Bridge [10de:02fd] (rev a1)
00:05.0 VGA compatible controller [0300]: nVidia Corporation C51 [Geforce Go 6150] [10de:0244] (rev a2)
00:09.0 RAM memory [0500]: nVidia Corporation MCP51 Host Bridge [10de:0270] (rev a2)
00:0a.0 ISA bridge [0601]: nVidia Corporation MCP51 LPC Bridge [10de:0260] (rev a3)
00:0a.1 SMBus [0c05]: nVidia Corporation MCP51 SMBus [10de:0264] (rev a3)
00:0a.3 Co-processor [0b40]: nVidia Corporation MCP51 PMU [10de:0271] (rev a3)
00:0b.0 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026d] (rev a3)
00:0b.1 USB Controller [0c03]: nVidia Corporation MCP51 USB Controller [10de:026e] (rev a3)
00:0d.0 IDE interface [0101]: nVidia Corporation MCP51 IDE [10de:0265] (rev f1)
00:0e.0 IDE interface [0101]: nVidia Corporation MCP51 Serial ATA Controller [10de:0266] (rev f1)
00:10.0 PCI bridge [0604]: nVidia Corporation MCP51 PCI Bridge [10de:026f] (rev a2)
00:10.1 Audio device [0403]: nVidia Corporation MCP51 High Definition Audio [10de:026c] (rev a2)
00:14.0 Bridge [0680]: nVidia Corporation MCP51 Ethernet Controller [10de:0269] (rev a3)
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration [1022:1100]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map [1022:1101]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller [1022:1102]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control [1022:1103]
07:05.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
07:05.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
07:05.2 System peripheral [0880]: Ricoh Co Ltd R5C843 MMC Host Controller [1180:0843] (rev 0a)
07:05.3 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 05)
07:05.4 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev ff)

---

### Post by Ayuthia on 2010-03-02
When you said that you checked it, what did you mean?  From the information that you provided, it looks like the device is no longer there.

I am also noticing that you have a dv6000 series laptop.  I know that there is an issue with the wireless card with some of the dv6000 series laptop.  I had that problem with mine (dv6338se) and ended up having to get the motherboard replaced (it was part of a limited warranty recall).  My problem was that the wireless card would sometimes appear and sometimes it was gone.

---

