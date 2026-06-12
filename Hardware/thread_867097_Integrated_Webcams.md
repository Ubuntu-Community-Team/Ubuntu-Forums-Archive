---
title: "Integrated Webcams"
date: 2008-07-22
forum: Hardware
---

### Post by vancedus on 2008-07-22
Hi, I am pretty new to Linux and I was just wondering if there is anyway to get the integrated webcam in my Asus to run? The webcam is a Genesys Logic.  I have Ubuntu 8.04, please help.  thank you

---

### Post by sergiom99 on 2008-07-23
please post the outputs of:
lspci
lsusb

Cheers.

---

### Post by vancedus on 2008-07-23
Here is lspci

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M G (rev a1)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller (rev 12)
03:00.0 SATA controller: JMicron Technologies, Inc. JMicron 20360/20363 AHCI Controller (rev 02)
04:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN Network Connection (rev 61)
07:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
07:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev ff)


And here is the second one 

Bus 004 Device 001: ID 0000:0000  
Bus 007 Device 003: ID 05e3:0503 Genesys Logic, Inc. 
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 147e:2016  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000 
Thank you

---

### Post by sergiom99 on 2008-07-24
heres your webcam: 
```
Bus 007 Device 003: ID 05e3:0503 Genesys Logic, Inc. 
```

Searching the forums for it, found this threads:
[http://ubuntuforums.org/showthread.php?t=581307&highlight=Genesys+Logic+webcam](http://ubuntuforums.org/showthread.php?t=581307&highlight=Genesys+Logic+webcam)

[http://ubuntuforums.org/showthread.php?t=740405&highlight=Genesys+Logic+webcam](http://ubuntuforums.org/showthread.php?t=740405&highlight=Genesys+Logic+webcam)

Hope this helps.

---

### Post by vancedus on 2008-07-24
thanks for the help.  I actaully couldn't find a solution in the first link, there is quite a bit there, and the link that worked for the user in the second link is no longer available.  If there is anything els anyone could do it would be great.  Thank you.

---

### Post by sergiom99 on 2008-07-24
there were other hits when I searched. Try searching for Genesys Logic webcam in the whole forums.

---

### Post by nol_faich on 2008-07-24
Hello !

Please go here : 
[_[COLOR="Blue"]http://ubuntuforums.org/showthread.php?p=5451750_[/COLOR]]("http://ubuntuforums.org/showthread.php?p=5451750")

Any help and tester is very much appreciated.

---

