---
title: "Losing internet connection"
date: 2008-08-08
forum: General Help
---

### Post by Rakanishu on 2008-08-08
With Ubuntu, I sometimes lose my connection to the internet.
Sometimes everything works, but while surfing it might just happen that I can't connect to websites.

No error messages at all. Even though once when I had rebooted from XP the connection info only showed zeroes.

---

### Post by tamoneya on 2008-08-08
what do you have for a NIC?  Run these commands so we can get the general specs of your system:```
sudo lshw -sanitize -C network
ifconfig
```

---

### Post by Rakanishu on 2008-08-08
> description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: [REMOVED]
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=[REMOVED] latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s

and from ifconfig:> 
eth0      Link encap:Ethernet  HWaddr 00:1d:92:f6:ec:cf  
          inet addr: LEGIT IP  Bcast:LEGIT IP  Mask:LEGIT IP
          inet6 addr: SOME inet6 ADDRESS Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:970 errors:0 dropped:2047800421 overruns:0 frame:0
          TX packets:626 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:974047 (951.2 KB)  TX bytes:77745 (75.9 KB)
          Interrupt:219 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1646 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1646 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:69132 (67.5 KB)  TX bytes:69132 (67.5 KB)

I am typing this with Ubuntu now, after a reboot from XP. So the problem seems to be intermittent.

---

### Post by tamoneya on 2008-08-08
hmm this appears to be a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221499](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221499)  Unfortunately this means there isnt all that much you can do about it.

---

### Post by StOoZ on 2008-08-08
I had that , solved that issue by removing this line :
> iface eth0 inet manual
from interfaces file.
just type in the terminal:
> sudo gedit /etc/network/interfaces

and put # at the beginning of that line.

---

### Post by Rakanishu on 2008-08-13
> **tamoneya said:**
> hmm this appears to be a known bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221499](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/221499)  Unfortunately this means there isnt all that much you can do about it.

When will it be solved then? Seems like quite a big bug since many people use this NIC.

---

### Post by Rakanishu on 2008-08-14
I should add that I am using a wireless router.
I had the problem just now, and I changed IP by unplugging the router for 20 min so that the DHCP was updated.

It worked now, but dunno if it is the same as the other problem?

---

### Post by Rakanishu on 2008-08-17
Turned out that was an entirely other problem.
I have to release DHCP lease everytime I change from Windows to Ubuntu.

But that has nothing to do with the disconnections when I do get online with Ubuntu.

---

