---
title: "Ethernet not working on Dell Latitude E5420"
date: 2014-12-31
forum: Hardware
---

### Post by Yizi on 2014-12-31
All, having issues with a clean install of 14.04 on my Dell. The ethernet adapter is not recognised but the wifi works fine. Here's my lspci

```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
00:1c.5 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 6 (rev b4)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 [Taylor Peak] (rev 34)
09:00.0 FireWire (IEEE 1394): O2 Micro, Inc. 1394 OHCI Compliant Host Controller (rev 05)
09:00.1 SD Host controller: O2 Micro, Inc. Integrated MMC/SD controller (rev 05)
09:00.2 Mass storage controller: O2 Micro, Inc. O2 Flash Memory Card (rev 05)
```

ifconfig shows:

```
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2834 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2834 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:304867 (304.8 KB)  TX bytes:304867 (304.8 KB)

wlan0     Link encap:Ethernet  HWaddr 08:11:96:ef:44:f8  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::a11:96ff:feef:44f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20660 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17182387 (17.1 MB)  TX bytes:3020969 (3.0 MB)

```

Any leads would be great, thanks

---

### Post by Yizi on 2014-12-31
Now my hard drive is not even recognised after the reboot, I tested the hard drive using a external caddy and it functions fine but now the BIOS doesn't even recognise it, I think the computer is falling apart.

---

