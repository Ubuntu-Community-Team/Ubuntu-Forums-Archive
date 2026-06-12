---
title: "No Wi-Fi, Realtek RT8187E on Ubuntu 8.10"
date: 2009-01-29
forum: Hardware
---

### Post by angus7 on 2009-01-29
I recently bought a MSI Wind U100. The instalation of Ubuntu 8.10 went smoothly. The only problem is that my WLAN module is not working properly. This is a excerpt from lspci -v listing

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
	Subsystem: Micro-Star International Co., Ltd. Device 6894
	Flags: bus master, fast devsel, latency 0, IRQ 10
	I/O ports at b000 [size=256]
	Memory at dfc00000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>

and the listing from lshw -C network

*-network UNCLAIMED
       description: Network controller
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 22
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

As you can see the module is recognized but the network manager completely ignores it.
I have checked the forum and there are a lot of helpful posts on Realtek RTL8187B and RTL8187L. But they are USB WLAN NIC's and RTL8187E is ceartinly not. Would following the guides for those models (and winging it when necessary) constitute a smart move?
I am not a absolute beginner when it comes to Ubuntu but I am certainly not a pro. If there is some solution to my problem with me not needing to muck about with ndiswrapper?:)

---

### Post by martinbaselier on 2009-01-29
I have an RTL8187B and it's implemented in the current kernel. They are both usb-devices though, so they will not help you. I fear you will have to use ndiswrapper. And it's probably going to be a bit of trial and error to get it working properly. Or maybe you're lucky and it works on first try. Couldn't find any info in English on the rtl8187E

EDIT: saw in your post it is recognised as an RTL8187SE. Try googling on that + linux. There's enough info on it available. Following the guide for a card you don't have will not do you much good. There are some experimental drivers out there. You can probably get one of them to work if you compile it yourself.

---

