---
title: "Drivers for TP-LINK TG-3468 NIC"
date: 2021-10-08
forum: Hardware
---

### Post by bglinkerman on 2021-10-08
I purchased the TP-LINK TG-3468 as I read a number of reviews saying that the NIC works with linux. I've been working that last several evenings to get the card working with no luck. I was hoping someone could give me a hand. Here is some relevant information.

[FONT=courier new]```
# lspci -d 10ec:8161 -v
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Device 8161 (rev 15)
Subsystem: Realtek Semiconductor Co., Ltd. Device 8168
Flags: bus master, fast devsel, latency 0, IRQ 3
I/O ports at e000 [size=256]
Memory at f7c04000 (64-bit, non-prefetchable) [size=4K]
Memory at f7c00000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [40] Power Management version 3
Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
Capabilities: [70] Express Endpoint, MSI 01
Capabilities: [b0] MSI-X: Enable- Count=4 Masked-
Capabilities: [d0] Vital Product Data
Capabilities: [100] Advanced Error Reporting
Capabilities: [140] Virtual Channel
Capabilities: [160] Device Serial Number 01-00-00-00-68-4c-e0-00
Capabilities: [170] Latency Tolerance Reporting
Capabilities: [178] L1 PM Substates
```

```
 # lspci -d 10ec:8161 -q
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 15)
```

```

# lshw -C network
*-network UNCLAIMED
description: Ethernet controller
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:02:00.0
version: 15
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress msix vpd bus_master cap_list
configuration: latency=0
resources: ioport:e000(size=256) memory:f7c04000-f7c04fff memory:f7c00000-f7c03fff
*-network
description: Ethernet interface
physical id: 2
logical name: eth2
serial: c0:56:27:90:68:41
capabilities: ethernet physical
configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=192.168.1.34 link=yes multicast=yes
```[/FONT]


I tried installing r8161-dkms but that didn't seem to help.

```
 [FONT=courier new]# apt-get install r8161-dkms[/FONT]
```[FONT=courier new]


```
# modinfo r8168
filename: /lib/modules/3.13.0-125-generic/updates/dkms/r8168.ko
version: 8.037.00-NAPI
license: GPL
description: RealTek RTL-8168 Gigabit Ethernet driver
author: Realtek and the Linux r8168 crew <netdev@vger.kernel.org>
srcversion: 4B9CB513BB22516F2449F45
alias: pci:v00001186d00004300sv00001186sd00004B10bc*sc*i*
alias: pci:v000010ECd00008168sv*sd*bc*sc*i*
depends:
vermagic: 3.13.0-125-generic SMP mod_unload modversions
parm: eee_enable:int
parm: speed:force phy operation. Deprecated by ethtool (8). (ushort)
parm: duplex:force phy operation. Deprecated by ethtool (8). (int)
parm: autoneg:force phy operation. Deprecated by ethtool (8). (int)
parm: aspm:Enable ASPM. (int)
parm: s5wol:Enable Shutdown Wake On Lan. (int)
parm: rx_copybreak:Copy breakpoint for copy-only-tiny-frames (int)
parm: use_dac:Enable PCI DAC. Unsafe on 32 bit PCI slot. (int)
parm: debugebug verbosity level (0=none, ..., 16=all) (int)
```
[/FONT]

---

### Post by mitesh.agrwl on 2021-10-10
There are multiple versions of the is card. V1-V4. TP-Link website shows Linux support for first version (V1) only. Contact the vendor support for clarification.

---

### Post by marc-flexicyber on 2022-01-09
Hi,

Is this problem solved?

I have a NIC tp link TG 3468 running on Debian.

lshw -class network -short
/0/100/1c/0      enp1s0     network        Realtek Semiconductor Co., Ltd.

lshw -class network
description: Ethernet interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 15
       serial: 6c:5a:b0:5a:a2:6c
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp aui bnc mii fibre 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 duplex=full ip=192.168.123.3 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:16 ioport:3000(size=256) memory:90304000-90304fff memory:90300000-90303fff
  *-network DISABLED



lspci - k
1:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Device 8161 (rev 15)
	Subsystem: Realtek Semiconductor Co., Ltd. Device 8168
	Kernel driver in use: r8169
	Kernel modules: r8169

Brgrds,

Marc

---

