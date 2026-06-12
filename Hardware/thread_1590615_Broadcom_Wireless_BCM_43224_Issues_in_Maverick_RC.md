---
title: "Broadcom Wireless BCM 43224 Issues in Maverick RC"
date: 2010-10-08
forum: Hardware
---

### Post by isoscelesrectangle on 2010-10-08
Hi all! 
I have a Dell Studio 1458. I just installed Lucid, then out of curiosity installed Maverick RC. The Broadcom 43224 isn't working in Lucid, and in Maverick, even after I went to System>Administration>Additional Drivers and installed the Broadcom STA driver. 
This is my lspci output: 

```
kevin@kevin-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DMI (rev 11)
00:03.0 PCI bridge: Intel Corporation Core Processor PCI Express Root Port 1 (rev 11)
00:08.0 System peripheral: Intel Corporation Core Processor System Management Registers (rev 11)
00:08.1 System peripheral: Intel Corporation Core Processor Semaphore and Scratchpad Registers (rev 11)
00:08.2 System peripheral: Intel Corporation Core Processor System Control and Status Registers (rev 11)
00:08.3 System peripheral: Intel Corporation Core Processor Miscellaneous Registers (rev 11)
00:10.0 System peripheral: Intel Corporation Core Processor QPI Link (rev 11)
00:10.1 System peripheral: Intel Corporation Core Processor QPI Routing and Protocol Registers (rev 11)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
02:00.0 VGA compatible controller: ATI Technologies Inc Manhattan [Mobility Radeon HD 5000 Series]
02:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
03:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
06:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-Core Registers (rev 04)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 04)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 04)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 04)
ff:03.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller (rev 04)
ff:03.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Target Address Decoder (rev 04)
ff:03.4 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Test Registers (rev 04)
ff:04.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Control Registers (rev 04)
ff:04.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Address Registers (rev 04)
ff:04.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Rank Registers (rev 04)
ff:04.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 0 Thermal Control Registers (rev 04)
ff:05.0 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Control Registers (rev 04)
ff:05.1 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Address Registers (rev 04)
ff:05.2 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Rank Registers (rev 04)
ff:05.3 Host bridge: Intel Corporation Core Processor Integrated Memory Controller Channel 1 Thermal Control Registers (rev 04)
```
I've been tackling this problem for the better half of the day, so if anyone can help me out I'll be extremely grateful! 
Cheers, 
The IsoscelesRectangle

---

### Post by Peter09 on 2010-10-08
For my broadcom card (whose number I cannot remember) there were two drivers available in the Hardware menu - one worked the other did not, its worth a check.

---

### Post by isoscelesrectangle on 2010-10-08
Yeah went to Additional Drivers again to check. Only found: 
Broadcom STA Wireless Driver
Says it supports: 
> These package contains Broadcom 802.11 Linux STA wireless driverfor use with Broadcom's BCM4311-, BCM4312-, BCM4321-, andBCM4322-based hardware.

---

### Post by Peter09 on 2010-10-08
Can you post the output of the terminal commands
 
```
ifconfig
```
and
```
lshw -C network
```
 
Do this without the hardwired link connected.

---

### Post by Peter09 on 2010-10-08
Had a quick browse and came across this site
 
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
 
According to this site - there is not date on this information - your hardware is not yet supported.

---

### Post by isoscelesrectangle on 2010-10-08
Thank you Peter09, however it can't hurt to try right? ;)
ifconfig output: 
```

eth0      Link encap:Ethernet  HWaddr 00:24:e8:83:cb:2c  
          inet6 addr: fe80::224:e8ff:fe83:cb2c/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:447 errors:0 dropped:0 overruns:0 frame:0
          TX packets:479 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:379411 (379.4 KB)  TX bytes:57814 (57.8 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:33 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2216 (2.2 KB)  TX bytes:2216 (2.2 KB)
```
lshw -C network output: 
```
kevin@kevin-laptop:~$ sudo lshw -C network
[sudo] password for kevin: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:24:e8:83:cb:2c
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.110 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:52 memory:f0300000-f030ffff
  *-network DISABLED
       description: Wireless interface
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: f0:7b:cb:5e:16:ff
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:18 memory:f0400000-f0403fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 4
       logical name: wwan0
       serial: 02:80:37:ec:02:00
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=Mobile Broadband Network Device link=yes multicast=yes
```
Thank you so much!

---

### Post by Peter09 on 2010-10-08
Some good news
 
[http://www.daemonnews.org/2010/09/10/linux-wi-fi-gets-easier-with-new-broadcom-driver.html](http://www.daemonnews.org/2010/09/10/linux-wi-fi-gets-easier-with-new-broadcom-driver.html)

---

### Post by isoscelesrectangle on 2010-10-08
Woops! Turns out the Ubuntu driver IS compatible! I turned off the wireless card in Windows, and since the function key didn't work in Ubuntu, I can only turn on and off the wireless card in Windows. 

Sorry if I wasted your time. :P

---

### Post by Carl.Spackler on 2010-10-08
I have the same model number card in my HP DV7 and it works perfectly without even downloading from the internet. Glad you got it working! :)

---

