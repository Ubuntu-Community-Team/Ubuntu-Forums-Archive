---
title: "Ubuntu 12.10 upgrade Monitor not working with Gateway MT6840 Laptop"
date: 2012-12-29
forum: Hardware
---

### Post by aconsuma on 2012-12-29
Hello,

I have an old GatewayMT6840 laptop and recently installed Ubuntu 12.10.  When I connect my Dell monitor to the computer the screen goes black and it is super slow.  I've been reading that Ubuntu 12.10 doesn't support 2D unity anymore. [http://askubuntu.com/questions/134346/why-is-unity-2d-being-discontinued](http://askubuntu.com/questions/134346/why-is-unity-2d-being-discontinued)

I am not sure if my **Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) **graphics card is able to handle 3d unity.

Any ideas?  Thanks!!!


  	 	 	 	 	 	   **uname -a **
  
  	 	 	 	 	 	   Linux xxxxxxx-**MT6840** 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:52:46 UTC 2012 i686 i686 i686 GNU/Linux 
 

 **lspci **
 

 00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03) 
 00:02.0 VGA compatible controller: **Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03) **
 00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03) 
 00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02) 
 00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02) 
 00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02) 
 00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02) 
 00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02) 
 00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02) 
 00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02) 
 00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02) 
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
 00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02) 
 00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02) 
 00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 02) 
 00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02) 
 02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14) 
 03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02) 
 04:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller 
 04:09.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller 
 04:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)

---

### Post by aconsuma on 2012-12-30
Any ideas?

---

### Post by ahallubuntu on 2012-12-30
Any reason you went with 12.10 instead of 12.04 LTS for an old laptop?  12.04 LTS will be supported much longer than 12.10 anyway - plus as you suggest perhaps Unity 2D isn't viable in 12.10?

I guess I'd try 12.04 LTS instead and see if it works better; if so, stick with it.

---

### Post by aconsuma on 2012-12-31
I didn't realize 2D was not being supported in 12.10 or that 12.04 is being supported longer.

---

