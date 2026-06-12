---
title: "Looking for good WiFi PCI-E card with Linux support"
date: 2018-09-22
forum: Hardware
---

### Post by smashcat on 2018-09-22
Hi, I'm looking for recommendations for a good PCI-E WiFi card with A+C support. Something like [https://www.asus.com/uk/Networking/PCE-AC88/](https://www.asus.com/uk/Networking/PCE-AC88/) but with proper driver support (that card is only supported at very low speeds in Linux, so is not usable - I've tried it :) ).

I need it to replace Ethernet, as I'm removing all my homeplugs that can not use the full speed of my broadband connection. The above card gives me 388Mbps on windows (it managed only 1.6Mbps under Linux :) ) at around 10 meters from my WiFi hub.

---

### Post by markackerman8@gmail.com on 2018-09-24
I have installed Linux/Ubuntu on over a hundred machines and in only 1 case in the past 5-6 years has the WiFi ever been an unsolvable issue either for speed  or drivers, and the one time was a very low end Hp (and likely more my friends Internet speed).

Not the answer your looking for but trying to help, Mark
p.s. this is cutting edge PCIe from my Omen X working fine
 *-network
                description: Wireless interface
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:6f:00.0
                logical name: wlo1
                version: 00
                serial: 74:40:bb:2e:0c:51
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8822be driverversion=4.15.0-35-generic firmware=N/A ip=192.168.1.69 latency=0 link=yes multicast=yes wireless=IEEE 802.11

---

### Post by SeijiSensei on 2018-09-24
This one uses an Intel chipset which is [well-supported]("https://www.intel.com/content/www/us/en/support/articles/000005511/network-and-i-o/wireless-networking.html") in the Linux kernel:

[https://www.newegg.com/Product/Product.aspx?Item=9SIADXZ5UB1660](https://www.newegg.com/Product/Product.aspx?Item=9SIADXZ5UB1660)

DK if it's available in the UK.  The list of PCI-E adapters with AC wireless only has [four entries at NewEgg]("https://www.newegg.com/Product/ProductList.aspx?Submit=ENE&IsNodeId=1&N=100158094%20600484864%20600546658%20600546660%20600014297"), and three of them are from this manufacturer.  They all happen to be on-sale right now, too.

---

### Post by markackerman8@gmail.com on 2018-09-24
I have installed Linux/Ubuntu on over a hundred machines and in only 1 case in the past 5-6 years has the WiFi ever been an unsolvable issue either for speed  or drivers, and the one time was a very low end Hp (and likely more my friends Internet speed).

Not the answer your looking for but trying to help, Mark
p.s. this is cutting edge PCIe from my Omen X working fine
 *-network
                description: Wireless interface
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:6f:00.0
                logical name: wlo1
                version: 00
                serial: 74:40:bb:2e:0c:51
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=rtl8822be driverversion=4.15.0-35-generic firmware=N/A ip=192.168.1.69 latency=0 link=yes multicast=yes wireless=IEEE 802.11

---

