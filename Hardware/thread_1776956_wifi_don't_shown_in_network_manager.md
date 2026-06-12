---
title: "wifi don't shown in network manager"
date: 2011-06-07
forum: Hardware
---

### Post by robingd on 2011-06-07
Hi all,i have installed ubuntu 11.04 on Lenovo v560, drivers manager find me some broadcast drivers  i installed it, but after rebut , wifi was no available in network manager , there no wifi networks at all ( .

iwconfig 
```

lo        no wireless extensions.

eth0      no wireless extensions.

```by moment before rebut  it has some eth1 with wifi .


i've try to use Ndiswrapper ... it doesn't work for me ( 
then i tried madwifi driver - the result was same



```
rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
rfkill unblock all
rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no

```

```
lspci 
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
03:00.0 Ethernet controller: Atheros Communications AR8131 Gigabit Ethernet (rev c0)
04:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

help please with this trouble (

```
 sudo lshw -C Network
description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c0
       serial: f0:de:f1:2a:aa:a1
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.1.104 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f2400000-f243ffff ioport:3000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f2500000-f2503fff

```

---

