---
title: "Cannot enable Linksys NIC EG1032v3 – rtl8169S chip"
date: 2008-03-01
forum: Hardware &amp; Laptops
---

### Post by richo132 on 2008-03-01
Hi, I would appreciate some help to get my Linksys Gbit NIC working.

Basic config: Ubuntu 7.10 server (2.6.22) on an IBM Netvista (1Ghz Pentium 3)
I have just done a clean install with only the EG1032 installed as ETH0.
LEDs on this NIC light up after cold boot, but turn off when the OS starts to load.

What I have done:
During a clean install set static IP as 192.168.0.5, gateway as 192.168.0.1
Install was slow - waited for timeouts on all network access
Then:
uname –r (to get kernel version)
apt-get install build-essential linux-headers-2.6.22-14-server  

Downloaded r8169-6.005.00.tar.bz2 from Realtek
Followed the included instructions to untar the file, then
make clean modules 
make install
depmod –a
insmod ./src/r8169.ko

All good – but ETH0 didn’t work :(

NB: To get useful screen caps for this post, I then added a 100Mbit NIC with rtl8139 chip as ETH2. I edited /etc/network/interfaces to make eth2 the default and restarted the network. At this point an IP address was assigned by my DHCP server and ETH2 started to work.  

Some information about the current situation:

root@xtunes:~# lspci -v | grep ethernet -i -A8
01:08.0 Ethernet controller: Linksys Gigabit Network Adapter (rev 10)
Subsystem: Linksys EG1032 v3 Instant Gigabit Network Adapter
Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 18
I/O ports at 7400 [size=256]
Memory at febffe00 (32-bit, non-prefetchable) [size=256]
Expansion ROM at ff000000 [disabled] [size=128K]
Capabilities: [dc] Power Management version 2

01:0e.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
Subsystem: Realtek Semiconductor Co., Ltd. RT8139
Flags: bus master, medium devsel, latency 208, IRQ 17
I/O ports at 7800 [size=256]
Memory at febfff00 (32-bit, non-prefetchable) [size=256]
Capabilities: [50] Power Management version 2

root@xtunes:~# more /proc/interrupts
           CPU0
  0:        105   IO-APIC-edge      timer
  1:        714   IO-APIC-edge      i8042
  6:          3   IO-APIC-edge      floppy
  7:          0   IO-APIC-edge      parport0
  8:          3   IO-APIC-edge      rtc
  9:          1   IO-APIC-fasteoi   acpi
 12:          4   IO-APIC-edge      i8042
 14:      19065   IO-APIC-edge      libata
 15:        540   IO-APIC-edge      libata
 16:         36   IO-APIC-fasteoi   uhci_hcd:usb1
 17:      90597   IO-APIC-fasteoi   eth2
 19:          0   IO-APIC-fasteoi   Intel 82801BA-ICH2
NMI:          0
LOC:      70014
ERR:          0
MIS:          0
**- no entry for eth0 ??**

root@xtunes:~# lsmod | grep r8169
r8169                  32388  0
**- driver apparently loaded**

root@xtunes:~# ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:18:F8:0A:52:86
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:18 Base address:0x8e00

eth2      Link encap:Ethernet  HWaddr 00:40:F4:3C:A7:59
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::240:f4ff:fe3c:a759/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:58265 errors:0 dropped:0 overruns:0 frame:0
          TX packets:31626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:82692115 (78.8 MB)  TX bytes:2301877 (2.1 MB)
          Interrupt:17 Base address:0x6f00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:14 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1376 (1.3 KB)  TX bytes:1376 (1.3 KB)

root@xtunes:~# ethtool eth0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Half
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
        **Link detected: no**

root@xtunes:~# ethtool -i eth0
driver: r8169
version: 2.2LK
firmware-version:
bus-info: 0000:01:08.0
**- correct driver apparently bound to the NIC**

root@xtunes:~# more /etc/hosts
127.0.0.1       localhost
192.168.0.5     xtunes

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

root@xtunes:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth2
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth2

root@xtunes:~# more /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth2
iface eth2 inet dhcp
iface eth0 inet static
        address 192.168.0.5
        netmask 255.255.255.0
        network 192.168.0.0
        broadcast 192.168.0.255
        gateway 192.168.0.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 192.168.0.1

root@xtunes:~# lshw -C network
 ** *-network:0 DISABLED        //WHY ???**
       description: Ethernet interface
       product: Gigabit Network Adapter
       vendor: Linksys
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 10
       serial: 00:18:f8:0a:52:86
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half ip=192.168.0.5 latency=64 link=no maxlatency=64 mingnt=32 module=r8169 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: e
       bus info: pci@0000:01:0e.0
       logical name: eth2
       version: 10
       serial: 00:40:f4:3c:a7:59
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.13 latency=208 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

Any help would be appreciated, cheers.

---

