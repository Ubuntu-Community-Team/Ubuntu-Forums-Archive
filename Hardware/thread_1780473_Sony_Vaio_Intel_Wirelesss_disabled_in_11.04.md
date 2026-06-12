---
title: "Sony Vaio Intel Wirelesss disabled in 11.04"
date: 2011-06-12
forum: Hardware
---

### Post by major.tal on 2011-06-12
Hey all,

Wireless which was working perfectly in Ubuntu 10 is now disabled in 11.04. Dual boot to Vista verified the hardware is ok.

Reading related posts I applied the following:

sudo lshw -C network

> 06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)


rfkill list all
> 
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no



sudo lshw -C network

> 
  *-network               
       description: Ethernet interface
       product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth2
       version: 82
       serial: 90:1d:92:d9:d4:14
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-velocity driverversion=1.15 duplex=full ip=10.0.0.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 ioport:3000(size=256) memory:f8000000-f80000ff
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:b4:30:b1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:fa000000-fa001fff
tal@tal-VGN-FZ430E:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth2
       version: 82
       serial: 90:1d:92:d9:d4:14
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-velocity driverversion=1.15 duplex=full ip=10.0.0.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 ioport:3000(size=256) memory:f8000000-f80000ff
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:b4:30:b1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:fa000000-fa001fff


The hardware switch does not seem to function (not even the attached LED).

Wired Ethernet works well.

Please help? Laptop almost useless without wireless :(

---

### Post by mikewhatever on 2011-06-12
Can you post the outputs of the following:

```
ifconfig

dmesg | grep wlan0
```

---

### Post by major.tal on 2011-06-12
**ifconfig**

> 
eth2      Link encap:Ethernet  HWaddr 90:1d:92:d9:d4:14  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::921d:92ff:fed9:d414/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:191328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109195 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:243906733 (243.9 MB)  TX bytes:12525928 (12.5 MB)
          Interrupt:17 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5323 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5323 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2525373 (2.5 MB)  TX bytes:2525373 (2.5 MB)



**dmesg | grep wlan0**

> (nothing to quote - grep doesn't find anything)

---

### Post by mikewhatever on 2011-06-12
Right, how about this:
```
dmesg | grep iwlagn
```

The card seems to be identified correctly and the driver loaded, but for some reason, there is no wireless interface (should be wlan0).

---

### Post by major.tal on 2011-06-12
***_thanks for your prompt replies!!!_***

**dmesg | grep iwlagn**

> [   24.746249] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   24.746253] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   24.749541] iwlagn 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   24.749553] iwlagn 0000:06:00.0: setting latency timer to 64
[   24.757843] iwlagn 0000:06:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   24.796767] iwlagn 0000:06:00.0: device EEPROM VER=0x36, CALIB=0x5
[   24.796770] iwlagn 0000:06:00.0: Device SKU: 0Xb
[   24.797556] iwlagn 0000:06:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   24.797708] iwlagn 0000:06:00.0: irq 45 for MSI/MSI-X
[   24.942597] iwlagn 0000:06:00.0: loaded firmware version 228.61.2.24


---

### Post by mikewhatever on 2011-06-12
The output shows no errors, so I don't know why the interface is not up. Try brining it up manually with the following command:
```
sudo ifconfig wlan0 up
```

...to verify that it's up, run ifconfig.

---

### Post by major.tal on 2011-06-12
Progress!

The LED lit up and the interface is showing up on ifconfig (but no IP yet - I waited):

> eth2      Link encap:Ethernet  HWaddr 90:1d:92:d9:d4:14  
          inet addr:10.0.0.6  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::921d:92ff:fed9:d414/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:326875 errors:0 dropped:0 overruns:0 frame:0
          TX packets:240656 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:301872692 (301.8 MB)  TX bytes:34740296 (34.7 MB)
          Interrupt:17 Base address:0x3000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17038 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17038 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9171786 (9.1 MB)  TX bytes:9171786 (9.1 MB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:e0:b4:30:b1  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


I re-ran sudo lshw -C network and it is no longer disabled:

> 
  *-network               
       description: Ethernet interface
       product: VT6120/VT6121/VT6122 Gigabit Ethernet Adapter
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth2
       version: 82
       serial: 90:1d:92:d9:d4:14
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-velocity driverversion=1.15 duplex=full ip=10.0.0.6 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:17 ioport:3000(size=256) memory:f8000000-f80000ff
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 61
       serial: 00:1d:e0:b4:30:b1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:fa000000-fa001fff


How do I "activate" it at the IP level? How would I persist this? Why did it not auto-start?

---

### Post by mikewhatever on 2011-06-12
With the wireless interface up you should be able to connect to APs (Access Points), and to automate the process of bringing the interface up, you can just add the following to /etc/rc.local.
```
ifconfig wlan0 up
```

If you want to find out why wlan0 doesn't come up as it should, I'd recommend posting a thread in the Networking and Wireless subforum.

---

### Post by coffeecat on 2011-06-12
One thing to add. Sometimes if you do a warm reboot from one OS to the other, the loadable firmware gets left in an inconsistent state and is not reloaded properly. From what I've read this can affect wireless devices which require firmware loaded. One way to avoid this is always to do a cold boot into the OS that is affected.

---

### Post by major.tal on 2011-06-12
a. These are simple boots.
b. I can't get it to work (it doesn't apply DHCP or do anything at the IP level)
c. It just disappeared again! - I left the laptop for a few minutes. It was in screensaver mode when I came back and the wifi is gone again. I didn't logoff - all my apps are still running. sudo lshw -C network shows it DISABLED again and it doesn't exist in the ifconfig printout. "sudo ifconfig wlan0 up" started it again (yet still with no IP)...

Please help.

---

### Post by major.tal on 2011-06-12
Also, maybe there is a problem with the driver reading the mechanical wifi-on-off switch? and every time it is read the wireless is disabled (regardless of the mechanical state?)

---

### Post by mikewhatever on 2011-06-12
> **major.tal said:**
> Also, maybe there is a problem with the driver reading the mechanical wifi-on-off switch? and every time it is read the wireless is disabled (regardless of the mechanical state?)

Usually, if that's the case, it also shows in the output of 'rfkill'. Something is obviously wrong, but I don't know what.

---

