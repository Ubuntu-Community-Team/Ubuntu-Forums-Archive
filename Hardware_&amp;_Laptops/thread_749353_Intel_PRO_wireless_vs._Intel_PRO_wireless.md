---
title: "Intel PRO wireless vs. Intel PRO wireless"
date: 2008-04-08
forum: Hardware &amp; Laptops
---

### Post by blashyrkh on 2008-04-08
Okay here goes... first my setup.

* I have two routers (one from my ISP and a Wireless) connected. The Wireless is a D-Link and are connected after the ISP router. 
* I have one HP laptop with the Intel PRO wireless 3945ABG build in.
* I have Ubuntu 7.04 with restricted drivers for Intel 3945 enabled.

and then my problem:

When connecting to the internet my signal strength often drops to 0% for severel seconds, and it often happens when someone in my neighbourhood are also online. Annoying... sure, fixable... probably if I changed channels on my router, but that's not my main concern.

In my effort to negate my drop outs, i borrowed a Netgear WG111v2 wireless USB adapter, disabled the buildin HP wireless and plugged the Netgear into the USB slot, just to try it out. Imagine my suprise to see that this adapter (also with the Intel PRO wireless 3945ABG) worked flawlessly, no drop outs, but a slight reduced signal strength (around 70%, where my HP build in are about 85%). Strangely when using the Netgear USB, i get no drop outs even when others in my area is online, and i never changed any channels. 

Aren't the two alike? why does the restricted drivers work with the USB adapter, but not with the build in? Can I upgrade firmware on for the build in or something?

---

### Post by dstew on 2008-04-08
Compare the chipsets to see if you have the correct driver for the on-board wireless. To check the onboard, do```
lspci
```To check the USB wireless, do```
lsusb
```The command ```
lshw -class network
```will tell you which driver is connected to the current network device(s).

---

### Post by blashyrkh on 2008-04-08
Tried your approach, but doesn't seem to get any usefull infomation on the USB adapter (to me anyway ) ](*,)
As far as I can se my onboard uses v1.2 is this correct read? I can't see what version the USB adapter uses.

> **dstew said:**
> Compare the chipsets to see if you have the correct driver for the on-board wireless. To check the onboard, do```
lspci
```
winther@winther-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller AHCI (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GeForce Go 7400 (rev a1)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
07:05.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

> To check the USB wireless, do```
lsusb
```
winther@winther-laptop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)
Bus 001 Device 003: ID 0c45:62c0 Microdia 
Bus 001 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 09da:000e A4 Tech Co., Ltd 
Bus 003 Device 001: ID 0000:0000  

> The command ```
lshw -class network
```will tell you which driver is connected to the current network device(s).
winther@winther-laptop:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth1
       version: 02
       serial: 00:1b:77:33:1c:ad
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.0mp firmware=14.2 1:0 () latency=0 multicast=yes wireless=radio off
       resources: iomemory:d8000000-d8000fff irq:16
  *-network
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@05:00.0
       logical name: eth0
       version: 00
       serial: 00:1b:24:4f:5d:f6
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.15-k2-NAPI firmware=0.5-1 latency=0 multicast=yes
       resources: iomemory:da000000-da01ffff ioport:4000-401f irq:18
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:6c:b0:27:f4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.0.124 multicast=yes wireless=IEEE 802.11g

---

### Post by dstew on 2008-04-08
> 02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)This is your on-board wireless. It is using the ipw3945 driver, and assigned to the device name eth1> Bus 001 Device 005: ID 0846:6a00 NetGear, Inc. WG111 WiFi (v2)This is the USB wireless adapter. I cannot see which driver it is using, and it is assigned to the device name wlan0.> Aren't the two alike?They are not alike. The USB wireless has a Realtek chipset (RTL8187), and the Intel wireless has an Intel chipset. Apparently the Intel driver/chipset/hardware setup doesn't work as well as the Realtek setup, but it does work some. They are just different. I googled around to see if anybody has an idea on how to make the Intel card work better, but could not find anything substantial. If it did not work at all, that would be one thing, but to work poorly, that is harder to figure out. Sorry I don't have more advice for you.

---

### Post by sdennie on 2008-04-08
It's possible that switching from the ipw3945 driver to the iwl3945 driver for the intel card could fix your problem (it fixed various problems for myself and others with the same wifi card).  Unfortunately, I don't know if there is a straightforward way to do this in Ubuntu 7.04 but, some googling and searching on this message board should turn up something.

---

