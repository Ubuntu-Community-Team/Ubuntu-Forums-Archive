---
title: "Wireless doesn't connect"
date: 2011-05-18
forum: Hardware
---

### Post by HugotheWizard on 2011-05-18
I have the bcm4311 wireless driver on my latitude d620 with natty narwhal. When I try to connect it just says wireless network disconnected. This is my ```
sudo lshw -C network
  *-network               
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:18:8b:b5:ce:6f
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5752-v3.19 ip=24.13.187.152 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:43 memory:efcf0000-efcfffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:1a:92:3f:1b:4a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=410.2160 link=no multicast=yes wireless=IEEE 802.11bg

```

and 

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:8b:b5:ce:6f  
          inet addr:24.13.187.152  Bcast:24.13.187.255  Mask:255.255.255.0
          inet6 addr: fe80::218:8bff:feb5:ce6f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5961 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8016061 (8.0 MB)  TX bytes:1072884 (1.0 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:304 errors:0 dropped:0 overruns:0 frame:0
          TX packets:304 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22608 (22.6 KB)  TX bytes:22608 (22.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1a:92:3f:1b:4a  
          inet6 addr: fe80::21a:92ff:fe3f:1b4a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10424 (10.4 KB)  TX bytes:19923 (19.9 KB)
```

---

### Post by garvinrick4 on 2011-05-19
Connect using wired internet then:
Here it is in Synaptices open it type in bcm and install
Need bcmwl-kernel-source
need b43-fwcutter
right click on those 2 and hit install then hit the apply arrow.
Close:

Next:
Hit windows key and "A" and type in additional drivers click on it
and make sure enable. Might have to reboot.

---

