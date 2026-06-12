---
title: "Slow StarTech ExpressCard Gigabit Laptop NIC (EC1000S)"
date: 2014-03-18
forum: Hardware
---

### Post by sonny4 on 2014-03-18
I'm running Ubuntu 12.04 LTS 64 bit on my laptop, and I wanted a gigabit NIC. 

I purchased the StarTech ExpressCard (EC1000S) but the speeds are worst than my 100Mbps on-board NIC.

I check for additional drivers (nothing found).

Also, I ran: sudo vim /etc/network/interfaces:
Added:
auto eth1
iface eth1 inet static {all static IP info}

ifconfig is showing the correct IP, etc. and there's no IP conflict on my network.

My biggest issue I'm having is that the link speed steadily gets slower until its to a crawl.

Any help would be greatly appreciated. Thanks for you time.

---

### Post by varunendra on 2014-03-21
Welcome to the forums sonny4!

With the card connected and working, please install "ethtool" which is used to diagnose and change settings of Ethernet cards. To install it, open a terminal (Ctrl-Alt-T) and run the following command -
```
sudo apt-get install ethtool
```

Then post back the output of following commands -
```
uname -mr
sudo lshw -numeric -C network
ifconfig -a
sudo ethtool eth1
```
..assuming "**eth1**" is the logical name of the card in question. If it is something else, please change it accordingly in the last command.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by sonny4 on 2014-04-03
I apologize for the delay in responding. Don't know how I overlooked this response. Thank you so much for the input. 

Here's the output:

```

sonny@Ubuntu-Server:~$ uname -mr
3.11.0-18-generic x86_64
sonny@Ubuntu-Server:~$ sudo lshw -numeric -C network
SCSI                      
  *-network        
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10EC:8168]
       vendor: Realtek Semiconductor Co., Ltd. [10EC]
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth1
       version: 03
       serial: 00:0a:cd:24:42:f5
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl_nic/rtl8168d-2.fw ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:43 ioport:5000(size=256) memory:cd200000-cd200fff memory:c8000000-c8003fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10EC:8136]
       vendor: Realtek Semiconductor Co., Ltd. [10EC]
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:71:97:a6
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.100 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:44 ioport:3000(size=256) memory:c9010000-c9010fff memory:c9000000-c900ffff
  *-network DISABLED
       description: Wireless interface
       product: AR242x / AR542x Wireless Network Adapter (PCI-Express) [168C:1C]
       vendor: Qualcomm Atheros [168C]
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wlan0
       version: 01
       serial: 00:21:63:7e:31:ea
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=3.11.0-18-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:cb100000-cb10ffff
sonny@Ubuntu-Server:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:33:71:97:a6  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:33ff:fe71:97a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4079 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12790181 (12.7 MB)  TX bytes:578786 (578.7 KB)


eth1      Link encap:Ethernet  HWaddr 00:0a:cd:24:42:f5  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:cdff:fe24:42f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:309 errors:0 dropped:10 overruns:0 frame:0
          TX packets:59 errors:0 dropped:94 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:54477 (54.4 KB)  TX bytes:10136 (10.1 KB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:673 errors:0 dropped:0 overruns:0 frame:0
          TX packets:673 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:96991 (96.9 KB)  TX bytes:96991 (96.9 KB)


virbr0    Link encap:Ethernet  HWaddr 8e:dd:25:56:39:57  
          inet addr:192.168.122.1  Bcast:192.168.122.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


wlan0     Link encap:Ethernet  HWaddr 00:21:63:7e:31:ea  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


sonny@Ubuntu-Server:~$ sudo ethtool eth1
Settings for eth1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	                                     1000baseT/Half 1000baseT/Full 
	Link partner advertised pause frame use: Symmetric Receive-only
	Link partner advertised auto-negotiation: Yes
	Speed: 1000Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: pumbg
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes

```

---

### Post by sonny4 on 2014-04-03
Quick note, I had to use the old ethernet port to get online this time (couldn't get an internet connection from my the NIC in question...probably just wasn't patient enough).

---

### Post by varunendra on 2014-04-04
> **sonny4 said:**
> ```

sonny@Ubuntu-Server:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:33:71:97:a6  
          inet addr:**[COLOR="#FF0000"]192.168.1.100[/COLOR]**  Bcast:192.168.1.255  Mask:255.255.255.0
....
....
eth1      Link encap:Ethernet  HWaddr 00:0a:cd:24:42:f5  
          inet addr:**[COLOR="#FF0000"]192.168.1.100[/COLOR]**  Bcast:192.168.1.255  Mask:255.255.255.0

```

Two different interfaces with same IP address?

Either the above is a wrong interface configuration, or a kind of networking that I am not well-versed with. Could you please explain above?

If you are as clueless as I am, please post back the outputs of the following -
```
nm-tool
cat /etc/network/interfaces
```
If the interfaces are being controlled by Network Manager, then please also post two screenshots showing both interfaces' IPv4 configurations (Network Manager settings for the interfaces).

---

