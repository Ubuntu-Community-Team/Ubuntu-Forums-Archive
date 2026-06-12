---
title: "network adapter driver 100mbs"
date: 2023-08-18
forum: Hardware
---

### Post by phrenemy on 2023-08-18
I'm relatively new to Ubuntu, so I have little idea how to proceed.

I have an old HP system that i installed ubuntu on.
It has a network card, which should be running at 1000Mbs, but the system caps it at 100Mbs. I assume it's driver related.

So I think I need to know how to install the driver. I have no idea where to get it. I've seen various online references, but nothing seemed recent (at least 5 yrs old for many posts) and exactly on target with what I need.

I know the nic is a Realtek RTL8161

lspci | grep -i net 
tells me it's a Realtek RTL8111/8168/8411 PCI Gigabit Ethernet Controller

sudo dmesg | grep r816 yields:
[    2.441706] r8169 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[    2.457555] r8169 0000:04:00.0 eth0: RTL8168gu/8111gu, c0:7c:d1:ff:4a:bf, XID 509, IRQ 127
[    2.457560] r8169 0000:04:00.0 eth0: jumbo features [frames: 9194 bytes, tx checksumming: ko]
[    2.458677] r8169 0000:04:00.0 enp4s0: renamed from eth0
[   53.491489] Generic FE-GE Realtek PHY r8169-0-400:00: attached PHY driver (mii_bus:phy_addr=r8169-0-400:00, irq=MAC)
[   53.675501] r8169 0000:04:00.0 enp4s0: Link is Down
[   56.450902] r8169 0000:04:00.0 enp4s0: Link is Up - 100Mbps/Full - flow control off

thank you

---

### Post by TheFu on 2023-08-18
Realtek RTL8111/8168/8411 PCI Gigabit Ethernet Controller has about 20 different versions. Guess they were too lazy to change the marketing name.  There are 2 drivers to try.  RTL8168 and RTL8169. Both are already on the system.  Seems the r8169 isn't working, but that could be due to all sorts of things. For example, the jumbo frame setting looks to be too large. We can't just pick any number we like.  All the network gear needs to support the size we pick. 9000b is typically the limit for consumer switches, so 9194b is too large.

BTW, I don't know why you think it is a RTL8161 when it clearly is a Realtek RTL8111/8168/8411.   Also, there are easy ways to get more detailed information about the hardware and driver being used. Either of these commands should provide the needed details.
```

lshw -C network 
inxi -Nxxx
```

Drivers are tied to the kernel version, so that's always necessary.  **uname -r** will provide it.

Realtek commonly has issues.  If you don't want to deal with this again, you can spend $25 and get a cheap Intel PRO/1000 NIC that will "just work" and seems to always work for the last 10 yrs.
I know these work well:
[LIST]
[*]Intel i211
[*]Intel i210
[*]Intel 82575GB
[/LIST]
I have a few other models that work, but I'm in the process of retiring that box, so it isn't available.  Just be careful with the i217V or other intel NICs that end in a "V" like a i225V or i219V. Some of those have issues.

Often, things that appear to be network issues are really hardware problems.  Ensure you have a CAT5e or better cable. Try a different switch port. Do these things first. Every once in a while, a switch that has been working for years will have a port fail or start to fail.  I've had an 8-port switch smoke and die, once.  Since that happened, all my switches are made of metal and sit on a metal rack. No more plastic.

When you want to try different drivers, try to use the DKMS package version. This will register with the kernel update process and re-link the driver for every new kernel automatically (99.99% of the time). Makes life much easier.

---

### Post by phrenemy on 2023-08-18
Thank you. I will try these options. 
The naming scheme seems to strange, as you said, 20 different models. I wrote I had a RTL8161 because this is the specific spec listed from HP. I figured the rtl8168 might have been a difference in naming between where I live (Canada) and an international or US model. But I should've been more precise. 

uname -r
5.19.0-50-generic

lshw -C network
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 10
       serial: c0:7c:d1:ff:4a:bf
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.19.0-50-generic duplex=full firmware=rtl8168g-3_0.0.1 04/23/13 ip=192.168.50.69 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:18 ioport:d000(size=256) memory:df104000-df104fff memory:df100000-df103fff

I'll try switching to a different CAT6 cable. The rest of the cables are CAT7+.

---

### Post by TheFu on 2023-08-19
When posting terminal output, it really helps if you would wrap it in forum 'code' tags.  We are used to reading text as it looks in a terminal.  The Advanced editor has a button (#) for that.  Or you can use most of the other tags like bold, italics, underline, then replace the "B" with "CODE" and it will be the same as using the advanced editor.  I tend to use the 'quote' wrap, and replace that with 'code' - easier for me to select a larger word by double-clicking and start typing, but the mechanics aren't important.

```
driver=r8169 driverversion=5.19.0-50-generic duplex=full firmware=rtl8168g-3_0.0.1 04/23/13
version: 10
```

Seems odd to have the driver and firmware be different. Also, that firmware date seems odd to me. Does the locale in Canada really put the YY in the middle of a date like that?  I'm used to seeing YY/MM/DD or DD/MM/YY or the funky US version MM/DD/YY (which makes little sense!).  Let me see if that's expected by asking Mr. Google.

[https://ubuntu-mate.community/t/wired-ethernet-connection-periodically-drops/10967](https://ubuntu-mate.community/t/wired-ethernet-connection-periodically-drops/10967) seems very similar to the issue here.  After he said he'd try a different cable, he disappeared.  We don't know what the actual solution was, which is maddening, but I suspect it was a bad cable.  BTW, he had exactly the same NIC, including the same version. He was getting much worse connection, just 10Mb/s.

Many of the other Mr. Google answers lead back to having wifi AND ethernet enabled at the same time, so ensure wifi isn't enabled.

---

### Post by TheFu on 2023-08-19
Much cleaner.  See how columns are retained?
```
uname -r
5.19.0-50-generic

lshw -C network
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       **version: 10**
       serial: c0:7c:d1:ff:4a:bf
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes **driver=r8169** driverversion=5.19.0-50-generic duplex=full **firmware=rtl8168g-3_0.0.1** 04/23/13 ip=192.168.50.69 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:18 ioport:d000(size=256) memory:df104000-df104fff memory:df100000-df103fff

```

---

