---
title: "Howto power-off USB-Port on suspend2ram?"
date: 2016-09-17
forum: Hardware
---

### Post by private_lock on 2016-09-17
Hello!

I got myself a fancy new mouse ... wireless! After so many years tied by a cord :-)

There is just one thing ... on suspend2ram my old mouse would also power down (i.e. switch the red LED off and not react on buttons). The new mouse somehow doesn't get the suspend signal, the blue LED shines brightly. Moreover it would also resume the system on pressing any button. Over the last few days I read a lot on /sys/bus/usb/devices and tried a few things, at least it won't wake the computer anymore, though I have no idea what cured this missbehavior. But for now lets call it solved.

This leaves me with the power-issue: the mouse manual states, that the device goes to powersave after 8 minutes of inactivity (works) or by clicking a button after the receiver is off:
- when I unplug the receiver, it works
- when I switch the notebook off completely, it works
- when I suspend2ram, the receiver keeps a connection to the mouse and it refuses to go into powersave unless 8 minutes of inactivity are over
- no idea about suspend2disk (haven’t been able to use this in ages ...)

lsusb
```

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 5986:014c Acer, Inc 
Bus 003 Device 002: ID 13d3:3394 IMC Networks Bluetooth
Bus 003 Device 004: ID 062a:5918 Creative Labs 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

It reports as Creative Labs, though it is a Chinese model from "Easterntimes Tech".

lspci
```

00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller (rev 06)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller (rev 06)
00:02.0 VGA compatible controller: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller (rev 06)
00:03.0 Audio device: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller (rev 06)
00:14.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI (rev 05)
00:16.0 Communication controller: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 (rev d5)
00:1c.2 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 (rev d5)
00:1c.3 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 (rev d5)
00:1c.5 PCI bridge: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #6 (rev d5)
00:1d.0 USB controller: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 (rev 05)                                                              
00:1f.0 ISA bridge: Intel Corporation HM87 Express LPC Controller (rev 05)      
00:1f.2 SATA controller: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] (rev 05)                                    
00:1f.3 SMBus: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller (rev 05)                                                                  
01:00.0 3D controller: NVIDIA Corporation GK106M [GeForce GTX 765M] (rev ff)    
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5227 PCI Express Card Reader (rev 01)                                                       
04:00.0 Ethernet controller: Qualcomm Atheros Killer E220x Gigabit Ethernet Controller (rev 13)
05:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723AE PCIe Wireless Network Adapter

```

```

$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:        16.04
Codename:       xenial

$ uname -a
Linux Meerschweinchen 4.4.0-34-generic #53-Ubuntu SMP Wed Jul 27 16:06:39 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

```

So far I have only read about, but not installed powernap or any other tools, if they are not part of the default Kubuntu. But I played around with imwheel to make use of the thumb buttons on the side ... works like a charm.

Finally I repeat my question: Howto power-off USB-Port on suspend2ram?

Thanx
private_lock

---

