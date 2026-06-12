---
title: "Does it matter which NIC I use?"
date: 2021-04-08
forum: Hardware
---

### Post by dacromir on 2021-04-08
I'm learning how to use Ubuntu Server (20.04 LTS). I had an old desktop from nearly 10 years ago laying around, so I wiped the hard drive and put installed Ubuntu on it. It's working well now, but the NIC on the motherboard is limited to 100Mbps speeds, and I want to take advantage of my gigabit fiber. I'm planning on buying an ethernet network adapter to put in my PCIe slot.

Does it matter which brand I use? I ask because the USB wifi adapter I had laying around was a massive pain to set up. I struggled for hours trying to get the drivers to build, and finally bought a [different one]("http://www.amazon.com/gp/product/B00EQT0YK2") that was better supported in Ubuntu. I plugged it in and it worked instantly.

I'd like to avoid the same experience with my ethernet network adapter. Are there specific brands or cards that will work without setup or installing drivers? I'm happy to go for a $30 card instead of a $15 card if I can just plug it in and have it work.

---

### Post by CelticWarrior on 2021-04-08
You can't go wrong with Intel NICs.

---

### Post by Yellow Pasque on 2021-04-08
Do you have a PCI-e x1 slot or does it need to be USB?

---

### Post by dacromir on 2021-04-08
I'm using a PCIe x1 slot

---

### Post by Yellow Pasque on 2021-04-14
Sorry for late reply. I did not see your last response.

> Are there specific brands or cards that will work without setup or installing drivers?
I would say most of them would. LAN NIC's are less finicky than wifi chipsets when it comes to Linux. Most LAN NIC's are probably going to use some variant of Realtek RTL8111 series, and those will work fine. Intel LAN chipsets are known for using less CPU. I doubt most people would notice under normal circumstances, especially with more powerful CPU's.

You should avoid Realtek RTL8125 (2.5G) chips if you want a hassle-free experience with 20.04. Support for those is only with more recent kernels.

> You can't go wrong with Intel NICs

Yeah, Intel Gigabit chipsets have been supported well. I'm not sure about the newer/faster ones.
My mobo uses the Intel I211 chipset.

---

### Post by hk42 on 2021-04-15
I think it would be more future proof to add a USB3 PCIe card and a USB3 1Gbps Ethernet dongle.
In fact those are even better than 100Mbps ones when only used on USB2 ports.
Mine is using a RTL8153 chip

---

### Post by CelticWarrior on 2021-04-15
> **hk42 said:**
> I think it would be more future proof to add a USB3 PCIe card and a USB3 1Gbps Ethernet dongle.
In fact those are even better than 100Mbps ones when only used on USB2 ports.
Mine is using a RTL8153 chip

Please explain why this would be better (and more future proof) than adding an Ethernet **card**? Why the USB3.0 PCIe card plus a USB3.0 dongle combo?

---

### Post by hk42 on 2021-04-18
Just because using a PCIe gigabit Ethernet card seems less usefull
than a card  with several USB3 ports and it takes a complete slot.

---

### Post by CelticWarrior on 2021-04-18
> **hk42 said:**
> Just because using a PCIe gigabit Ethernet card seems less usefull
than a card  with several USB3 ports and it takes a complete slot.

It works a LOT better tough.
Experts seldom recommend USB Ethernet adapters for a very good reason, most are crap. For a slim notebook with only USB ports maybe an option but for a desktop, if you can avoid it - and you obviously can - than you should.

---

### Post by TheFu on 2021-04-18
I've had GigE realtek and maxell NICs fail or be really slow.  Some of the Realtek RTL8111 come in many, many, many, different versions - some work well out of the box, and others don't work at all, ever.  It becomes a hassle of trying to find the exact, correct driver and a few options to get non-working Realtek to work.

OTOH, I have Intel i210 and i211 and 82574L NICs. None have failed. All support GigE (920-940 Mbps) wired ethernet speeds.  They've all been plug and use.

Be very careful with any of the 2.5Gbps NICs regardless of vendor. Realtek and Intel both have less than great support today. Last fall, a few people tried to get the new Intel 2.5Gbps NICs working, but ended up buying a $25 **Intel PRO/1000 NIC** until the needed drivers worked and were provided by default.  Intel has published drivers, but for some reason those don't appear to work in Ubuntu - including 20.10.  Perhaps 21.04 will have support?

If you want to be future proof, jump to the Intel or Broadcom 10 Gbps NICs. That is a completely different level of networking. It will cost more and sometimes they don't use CAT7 ethernet cables, but fibre optic cables, so be careful if you go this route.  10Gbps routers/switches are more costly too, but much less than they were 10 yrs ago.

For newer laptops that don't have any ethernet port, I have a USB3-GigE adapter.  Ubuntu Server didn't recognize it, but the Desktop installers did. It uses the ax88179_178a driver. I don't see any vendor name, so you'd need to search by the chip and driver if you want to go that direction.  Mine has 3 USB3 ports in addition to the GigE. It uses a single old-USB3 "blue" port on the laptop.  I'd rather have built-in ethernet, but it does routinely show 922 Mbps to other systems on my LAN going through 1-2 cheap $18 GigE switches.  When traveling, I don't take this USB3 adapter.  I do bring a travel wifi-router which is tiny and provides a default blocking NAT router for all my wifi devices if only wired ethernet is available.  Some hotels don't have wifi everywhere, but still use wired ethernet in the rooms.

---

### Post by SeijiSensei on 2021-04-19
[https://www.newegg.com/Product/Productcompare?CompareItemList=9SIA4RE8NV1888%2C9SIA4RE8NV2264%2C9SIAH8W97S5016%2C9SIAM4SA8G3562](https://www.newegg.com/Product/Productcompare?CompareItemList=9SIA4RE8NV1888%2C9SIA4RE8NV2264%2C9SIAH8W97S5016%2C9SIAM4SA8G3562)

This one gets high marks. [https://www.amazon.com/Intel-EXPI9301CTBLK-1000Mbps-PCI-Express-Network/dp/B00830H91M](https://www.amazon.com/Intel-EXPI9301CTBLK-1000Mbps-PCI-Express-Network/dp/B00830H91M) It's a couple buck more expensive at Amazon, but you don't have to wait for it to be shipped from Hong Kong like the one at NewEgg does.

---

### Post by hk42 on 2021-04-19
> **TheFu said:**
> 
For newer laptops that don't have any ethernet port, I have a USB3-GigE adapter.  Ubuntu Server didn't recognize it, but the Desktop installers did. It uses the ax88179_178a driver. I don't see any vendor name, so you'd need to search by the chip and driver if you want to go that direction.  Mine has 3 USB3 ports in addition to the GigE. It uses a single old-USB3 "blue" port on the laptop.  I'd rather have built-in ethernet, but it does routinely show 922 Mbps to other systems on my LAN going through 1-2 cheap $18 GigE switches.

I agree with you
It seems to me that a computer with only on board 100Mbps will never take full advantage of a gigabit card.
But the global network should benefit of seeing few gigabits packets instead of more time consuming 100Mbps ones .
I have the same kind of USB3 hub with Gigabit Ethernet it seems a good solution for the price.
It only lacks a 5 V external supply and some LED's on the RJ45 port.

---

