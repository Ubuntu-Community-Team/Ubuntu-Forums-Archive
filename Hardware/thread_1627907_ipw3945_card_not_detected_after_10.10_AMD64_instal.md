---
title: "ipw3945 card not detected after 10.10 AMD64 install"
date: 2010-11-22
forum: Hardware
---

### Post by Kelon on 2010-11-22
NOOB
My ipw3945A/B/G card is not detected after Ubuntu 10.10 AMD64 install.
I have gone over multiple forums and tried many different techniques in forums and guides with no results. 
I have everything else working in my Lifebook S7110 using forums I've found and guides but this!
Does anyone have any Ideas?

It does not show up in lshw -c network

---

### Post by Fafler on 2010-11-22
Does it show up in lspci? Has it worked with Linux before?
It might be a OEM card with different vendor and device ID's, that isn't recognised by the driver.

---

### Post by Kelon on 2010-11-22
> **Fafler said:**
> Does it show up in lspci? Has it worked with Linux before?
It might be a OEM card with different vendor and device ID's, that isn't recognised by the driver.
Neither. It has shown up a couple of times in lshw but then disappears?

---

### Post by Kelon on 2010-11-22
> **Fafler said:**
> Does it show up in lspci? Has it worked with Linux before?
It might be a OEM card with different vendor and device ID's, that isn't recognised by the driver.
Here is my output from lshw -c network. The Texas Instrument is a pcmcia  Im about to try to install till I figure out the Intel 3945.  

*-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 12
       serial: 00:17:42:3d:40:76
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:42 memory:f0000000-f0003fff ioport:2000(size=256) memory:44000000-4401ffff
  *-network UNCLAIMED
       description: Network controller
       product: ACX 111 54Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 1
       bus info: pci@0000:09:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm cap_list
       configuration: latency=0
       resources: memory:48020000-48021fff memory:48000000-4801ffff

---

### Post by Fafler on 2010-11-22
Well, lspci only cares about which cards are physically present, so if it doesn't show up in lspci, it's either bad hardware or something BIOS/kernel/wireless card related. Have you confirmed the card to be working with another OS?

Is there a WIFI switch on the laptop?

---

### Post by Kelon on 2010-11-22
Yes there is a switch and I have tried it on and off. 
Here is my lspci

lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 12)
08:03.0 CardBus bridge: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller (rev 21)
08:03.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 01)
08:03.3 Bridge: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
08:03.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface

---

### Post by Kelon on 2010-11-22
the first line should be the driver for the 3945?
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)

---

### Post by justin whitaker on 2010-11-22
The first line is the CPU and memory handler. 

The Ethernet controller and wireless controllers are on separate lines (02,09). 

Did you try looking at the drivers for those, or try using the driver listed here?

[http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/)

---

### Post by Kelon on 2010-11-22
All of the documentation that I have read says that the driver is in all kernels after  [B]2.6.24
[/B]and in my files I have
 
/lib/firmware/iwlwifi-3945-2.ucode
/lib/modules/2.6.35-22-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko
/usr/src/linux-headers-2.6.35-22-generic/include/config

Are these not functional or do I just need to find out how to set it up right?

---

### Post by Fafler on 2010-11-22
You should have a entry similar to
```
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
```

Have you confirmed the card works with another OS?

---

### Post by Kelon on 2010-11-22
I will download and try windows tonight and get back to you.

---

### Post by Fafler on 2010-11-22
Before you do that, take the miniPCIe card out and put it back in. Also, go to the BIOS setup and load the default values.

---

### Post by Kelon on 2010-11-23
Ok so I have tried everything except putting windows on the system. The  card is part of the motherboard in the laptop so I can not disconnect  it, but I have reset the BIOS twice and done a reinstall. In all of the  documentation and forums that I have read It says that its common for  the 3945 to not show up. I think Im going to set up the  ACX 111 for now. I would really like to figure this out  though. I have switched all of my computers to linux distros with no  windows any more in the last couple of weeks and this is the only  problem I have had, so I'm pretty happy but would love to learn how to  deal with this.
Thanx for your help

---

