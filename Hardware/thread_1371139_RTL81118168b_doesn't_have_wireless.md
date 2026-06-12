---
title: "RTL8111/8168b doesn't have wireless"
date: 2010-01-03
forum: Hardware
---

### Post by g.zhen.ning on 2010-01-03
I have new laptop Thinkpad SL410 2842-5AC. the windows XP on it have wireless. but when I install Ubuntu 9.1 AMD64, wired connect is ok. but doesn't have wireless. So I searched a lot, like replace R8169 with R8168, enable wake-on-lan in BIOS.
almost anything on WEB I have been try.

iwconfig command return no wireless extension.
ispci command return a RTL8111/8168b.

I'm so despair., any thought would be appreciated.

---

### Post by Yellow Pasque on 2010-01-03
RTL8111/8169 is the Ethernet LAN, not the wireless. Please post output of:
```
sudo lshw -C network
```

---

### Post by g.zhen.ning on 2010-01-03
ning@ning:~$ sudo lshw -C network
[sudo] password for ning: 
  *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:f2200000-f2203fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 03
       serial: 00:26:9e:6f:ef:08
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:31 ioport:5000(size=256) memory:f2004000-f2004fff(prefetchable) memory:f2000000-f2003fff(prefetchable) memory:f2020000-f203ffff(prefetchable)
ning@ning:~$

------------------------------

---

### Post by Yellow Pasque on 2010-01-03
Do you know what kind of wireless chipset you have? Do you have a link to the windows driver?

---

### Post by derekmbarnes on 2010-01-03
"lshw" doesn't help with the wireless. Use "lspci" and look for "Network controller." This is your wireless device. Note down the device number and get back to us.

---

### Post by Yellow Pasque on 2010-01-03
> "lshw" doesn't help with the wireless.
lshw prints info for wireless devices and usually helps identify the chipset. As you can see above, Realtek chose to be vague with their product description in this case.
```
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
```

lshw for my wireless:
```
product: RTL8180L 802.11b MAC
vendor: Realtek Semiconductor Co., Ltd.
```

---

### Post by derekmbarnes on 2010-01-03
> **Temüjin said:**
> lshw prints info for wireless devices and usually helps identify the chipset. As you can see above, Realtek chose to be vague with their product description in this case.
```
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
```lshw for my wireless:
```
product: RTL8180L 802.11b MAC
vendor: Realtek Semiconductor Co., Ltd.
```

Duly noted. Sadly my lshw line showed the first set of code when I used it; lspci was much more helpful.

---

