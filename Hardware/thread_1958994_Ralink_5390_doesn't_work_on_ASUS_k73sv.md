---
title: "Ralink 5390 doesn't work on ASUS k73sv"
date: 2012-04-15
forum: Hardware
---

### Post by tocitox on 2012-04-15
Hello everyone,

I have an ASUS k73sv laptop with a ralink 5390 wireless adapter card. It seems that it is not recognized by Ubuntu 11.04 .

The output of lspci:

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)
03:00.0 Network controller: Ralink corp. Device 5390
04:00.0 Ethernet controller: Atheros Communications Device 1083 (rev c0)

```The output of ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 54:04:a6:25:9d:71  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5604:a6ff:fe25:9d71/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8870 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:10227935 (10.2 MB)  TX bytes:1430887 (1.4 MB)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1200 (1.2 KB)  TX bytes:1200 (1.2 KB)

```I followed exactly the instructions from here: [https://atinfinity.wordpress.com/2011/05/21/ralink-rt5390-wi-fi-driver-on-ubuntu-11-04/](https://atinfinity.wordpress.com/2011/05/21/ralink-rt5390-wi-fi-driver-on-ubuntu-11-04/) . Still doesn't work unofortunately...

Any help would be apreciated!

---

