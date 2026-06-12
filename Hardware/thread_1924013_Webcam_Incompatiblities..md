---
title: "Webcam Incompatiblities."
date: 2012-02-11
forum: Hardware
---

### Post by optima4 on 2012-02-11
So ever since i installed Ubuntu I have never had any luck with my webcam working. Has anyone else ever had this issue? At first I thought it was just my netbook. I tried Ubuntu 11.04, 11.10, and now on 10.10 same issue. So I picked up a separate webcam and micro phone. Other than picture quality is terrible I am still unable to record videos. 

if config -a
```
eth0      Link encap:Ethernet  HWaddr b8:70:f4:73:9e:00  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan0     Link encap:Ethernet  HWaddr b0:48:7a:96:d4:8d  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::b248:7aff:fe96:d48d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40900 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:79605238 (79.6 MB)  TX bytes:5665048 (5.6 MB)

```lspci
```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1)
02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01
```lspci -v
```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel

00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at 98180000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 60c0 [size=8]
    Memory at 80000000 (32-bit, prefetchable) [size=256M]
    Memory at 98000000 (32-bit, non-prefetchable) [size=1M]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, fast devsel, latency 0
    Memory at 98100000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at 98200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: 97000000-97ffffff
    Prefetchable memory behind bridge: 0000000090000000-0000000090ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 96000000-96ffffff
    Prefetchable memory behind bridge: 0000000091000000-0000000091ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 6080 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, medium devsel, latency 0, IRQ 20
    I/O ports at 6060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 6040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, medium devsel, latency 0, IRQ 22
    I/O ports at 6020 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, medium devsel, latency 0, IRQ 22
    Memory at 98204400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA Controller [AHCI mode] (rev 02) (prog-if 01 [AHCI 1.0])
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 42
    I/O ports at 60b8 [size=8]
    I/O ports at 60cc [size=4]
    I/O ports at 60b0 [size=8]
    I/O ports at 60c8 [size=4]
    I/O ports at 60a0 [size=16]
    Memory at 98204000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: medium devsel, IRQ 10
    I/O ports at 6000 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller: Atheros Communications Inc. AR8152 v1.1 Fast Ethernet (rev c1)
    Subsystem: Acer Incorporated [ALI] Device 034a
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at 97000000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 5000 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c

02:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
    Subsystem: Broadcom Corporation Device 0510
    Flags: fast devsel, IRQ 17
    Memory at 96000000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: brcmsmac, wl

```This is the camera and mic I bought. I know they are weak it was just to test this issue out. I actually have a perfectly good webcam in my netbook LT27 Gateway Netbook. 

**[Microphone]("http://www.amazon.com/gp/product/B002EQ6E9E/ref=oh_o01_s00_i00_details")**
**[Webcam]("http://www.amazon.com/gp/product/B0015TJNEY/ref=oh_o02_s00_i00_details")**
_______________________________________________________________________

I do not know which drivers I have ran since back in 10/11. I have ran quite a few and have just recently ran sudo apt-get install.

---

### Post by ahallubuntu on 2012-02-11
You webcam may be connected internally as a USB device - my built-in webcam in my Dell laptop is connected this way.

So do "lsusb" too to see if your webcam shows up there, like mine does.

---

### Post by optima4 on 2012-02-11
Well it is showing up for pics. And very bad quality I may add. But the video is still acting the same.

```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 009: ID 090c:71b3 Feiya Technology Corp. 
Bus 001 Device 008: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 001 Device 007: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 001 Device 006: ID 0cf3:9271 Atheros Communications, Inc. AR9271 802.11n
Bus 001 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 001 Device 003: ID 0402:7675 ALi Corp. 
Bus 001 Device 002: ID 1a40:0101 TERMINUS TECHNOLOGY INC. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

---

