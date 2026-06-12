---
title: "Wireless problem with Sony Vaio VGN-SR130N"
date: 2009-06-04
forum: Hardware
---

### Post by abdel.ms on 2009-06-04
I recently installed ubuntu 9.04 in my new Sony Vaio VGN-SR130N. The wireless is detected, I can connect to the network but I can't get access to any device or internet.

With wired network card all works fine. In Windows Vista with same network configuration the wireless is working.

Thanks in advance for your help.

Some information about my laptop:

**1)** lshw -C network output

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:ba:1c:85:da
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.22 firmware=N/A latency=0 module=sky2 multicast=yes
[B][COLOR="Blue"]  *-network
       description: Wireless interface
       product: Wireless WiFi Link 5100
[/COLOR][/B]       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wmaster0
       version: 00
       serial: 00:16:ea:5b:c2:8a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=10.15.4.27 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 6a:27:fb:54:d8:fc
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

**2)** system messages log

Jun  4 08:05:35 amartinez-vai kernel: [   10.655356] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
Jun  4 08:05:35 amartinez-vai kernel: [   10.655359] iwlagn: Copyright(c) 2003-2009 Intel Corporation
Jun  4 08:05:35 amartinez-vai kernel: [   10.655422] iwlagn 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
Jun  4 08:05:35 amartinez-vai kernel: [   10.655469] iwlagn 0000:04:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0x54
Jun  4 08:05:35 amartinez-vai kernel: [   10.677460] iwlagn 0000:04:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels

**3)**  wpa supplicant log

Trying to associate with 00:15:f9:28:d1:c0 (SSID='ciscbbIT03' freq=2452 MHz)
Associated with 00:15:f9:28:d1:c0
CTRL-EVENT-CONNECTED - Connection to 00:15:f9:28:d1:c0 completed (auth) [id=0 id_str=]
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS
CTRL-EVENT-SCAN-RESULTS

4) route without wired connection

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
link-local      *               255.255.0.0     U         0 0          0 wlan0
10.15.0.0       *               255.255.0.0     U         0 0          0 wlan0
default         10.15.0.1       0.0.0.0         UG        0 0          0 wlan0

5) route output with wired connection

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
link-local      *               255.255.0.0     U         0 0          0 wlan0
10.15.0.0       *               255.255.0.0     U         0 0          0 eth0
10.15.0.0       *               255.255.0.0     U         0 0          0 wlan0
default         10.15.0.1       0.0.0.0         UG        0 0          0 eth0

---

