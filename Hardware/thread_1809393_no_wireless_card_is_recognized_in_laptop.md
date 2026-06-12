---
title: "no wireless card is recognized in laptop"
date: 2011-07-21
forum: Hardware
---

### Post by jRdbRR on 2011-07-21
I suspect that the laptop's wireless card is not getting power, but i do not know how to check/fix that.  Here's my troubleshooting...

windows device manager showed no wireless adapter, even after searching for new hardware
I tried another wireless card from a different laptop, and the machine still does not see any wireless interface
windows device manager showed no wireless adapter, even after searching for new hardware
I loaded up linux (backtrack 5) lspci showed no wireless adapter, 

i am scouring the internet to no avail...
any ideas?

---

### Post by jRdbRR on 2011-07-21
here is my lspci readout      00:00.0 RAM memory: 
nVidia Corporation C51 Host Bridge (rev a2)   00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)    00:00.2 
RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)    00:00.3 
RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)    00:00.4 
RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)    00:00.5 
RAM memory: nVidia Corporation C51 Host Bridge (rev a2)    00:00.6 
RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)    00:00.7 
RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)    00:02.0 
PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)    00:03.0 
PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)    00:05.0 
VGA compatible controller: nVidia Corporation C51 [GeForce Go 6100] (rev a2)    00:09.0 
RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)    00:0a.0 
ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)    00:0a.1 
SMBus: nVidia Corporation MCP51 SMBus (rev a3)  00:0a.3 
Co-processor: nVidia Corporation MCP51 PMU (rev a3)    00:0b.0 
USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)    00:0b.1 
USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)    00:0d.0 
IDE interface: nVidia Corporation MCP51 IDE (rev f1)    00:0e.0 
IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)    00:10.0 
PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)    00:10.1 
Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)    00:14.0 
Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)    00:18.0 
Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration    00:18.1 
Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map    00:18.2 
Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller    00:18.3 
Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control

---

### Post by jRdbRR on 2011-07-21
.

---

### Post by dougalkerr on 2011-07-21
Even though the card does not appear to be getting picked up it is still worth downloading the Windows driver file and extracting the files to a folder so as to release the .inf driver file for the card. Then provided you have 'Windows Wireless drivers' program installed in Administration menu try to load the driver and see if your card is now seen. Reboot and see if anything works.
I just solved a problem today with an Atheros 5000 card built for XP on an Acer 3660 laptop and the WWD program picked up the file and detected the hardware straight off. Previously I had intermittent On/Off with the Wireless Card.
Good luck.

---

### Post by jRdbRR on 2011-07-21
thanks for your help, man, but according this [http://h30434.www3.hp.com/t5/Wireless-Internet-and-home/Support-HP-Compaq-Presario-F500-Wireless-down/td-p/172996/page/2](http://h30434.www3.hp.com/t5/Wireless-Internet-and-home/Support-HP-Compaq-Presario-F500-Wireless-down/td-p/172996/page/2) this laptop wireless adapter is screwed

---

