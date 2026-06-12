---
title: "Unable to connect to wireless network"
date: 2008-09-29
forum: Hardware
---

### Post by JustForKicks on 2008-09-29
Hi,

I have a Dell Vostro 1710 and have configured it to dual boot Vista and Ubuntu 8.04 LTS(32bit desktop) . I have got the wired network to work after installing Realtek drivers. 

But I am unable to connect to the wireless network.(using the Broadcom BCM4312) device.

I am trying to get it to work using the wl driver.

Details:

root@laptop15:~# uname -a
Linux laptop15 2.6.24-21-generic #1 SMP Mon Aug 25 17:32:09 UTC 2008 i686 GNU/Linux

root@laptop15:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
06:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
08:05.0 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
08:05.2 SD Host controller: O2 Micro, Inc. Integrated MMC/SD Controller (rev 02)
08:05.3 Mass storage controller: O2 Micro, Inc. Integrated MS/xD Controller (rev 01)
===================================================================================

root@laptop15:~# lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:1f:e2:81:69:b8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:59:b7:0e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.008.00-NAPI duplex=full ip=192.168.1.215 latency=0 link=yes module=r8168 multicast=yes port=twisted pair speed=100MB/s

===============================================================================

Relevant output from dmesg:
[   39.240430] ieee80211_crypt: registered algorithm 'NULL'
[   39.244529] ACPI: PCI Interrupt 0000:06:00.0[A] -> GSI 19 (level, low) -> IRQ 18
[   39.244545] PCI: Setting latency timer of device 0000:06:00.0 to 64
[   39.574923] ieee80211_crypt: registered algorithm 'TKIP'
[   39.575208] eth1: Broadcom BCM4315 802.11 Wireless Controller 5.10.27.6

===============================================================================
So it looks like the driver gets loaded properly and it must be an issue with the network configuration.

My /etc/network/interfaces contains this:
iface eth1 inet dhcp

wpa-ap-scan 1
wpa-pairwise TKIP
wpa-group TKIP
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid "Somename"
auto eth1

Also iwlist is able to obtain some info about the network:
root@laptop15:~# iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 00:1B:11:B0:78:10
                    ESSID:""
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:4/5  Signal level:-64 dBm  Noise level:-3 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s


=========================================================================

After all this, it is still not able to 
connect to the gateway/router/DHCP server.
root@laptop15:~# ping -c 4 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
From 192.168.1.215 icmp_seq=2 Destination Host Unreachable
From 192.168.1.215 icmp_seq=3 Destination Host Unreachable
From 192.168.1.215 icmp_seq=4 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2998ms
, pipe 3

I have tried every thing I know plus what I could find from google, but to no avail. So any help will be very welcome.

Thanks.

---

### Post by JustForKicks on 2008-09-29
Forgot to add that, I am able to connect to the wireless network in Vista.
So I guess that rules out hardware defects.

---

### Post by superprash2003 on 2008-11-06
try this [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

