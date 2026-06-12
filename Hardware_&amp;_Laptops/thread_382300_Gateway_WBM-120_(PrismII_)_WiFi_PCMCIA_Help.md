---
title: "Gateway WBM-120 (PrismII ?) WiFi PCMCIA Help"
date: 2007-03-11
forum: Hardware &amp; Laptops
---

### Post by etnpnys on 2007-03-11
Hi, I have a (slightly) older Gateway 450 SX4 laptop. Unfortunately, I bought the version without integrated WiFi, so I'm left here trying to get the Gateway WBM-120 PCMCIA device working.

The main problem - I believe - is that the device is not recognized as a wireless network device. When I open the "Network" utility, all I see is Eth0 (which is the wired NIC that I'm using right now) and the Modem. There is no wireless card listed at all...

However, if I go into "Hardware Information" (which is locking up right now for some reason...) it lists the card as the Gateway WBM-120 wireless network device. Also, if I open a terminal window and type "sudo lshw" it lists the device under the PCMCIA parent, but there's very minimal other information listed for the device. See below:

[COLOR="Blue"]           *-pcmcia:1
                description: CardBus bridge
                product: PCI1520 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 2.1
                bus info: pci@02:02.1
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: iomemory:e8205000-e8205fff irq:10
              *-network
                   description: WBM-120 Wireless Adapter
                   vendor: Gateway
                   physical id: 0
                   slot: Socket 1[/COLOR]

Also, typing "sudo pccardctl ident" gives me the following:

[COLOR="Blue"]Socket 0:
  no product info available
Socket 1:
  product info: "Gateway", "WBM-120 Wireless Adapter", "", ""
  manfid: 0x028a, 0x55b0
  function: 6 (network)[/INDENT][/COLOR]

Am I wrong in thinking that the device is recognized, but not using a proper driver? Through the research that I have done, I have found that the Orinoco driver and the PrismII driver should work, but I have no idea how to force a different driver into the system. See this link (if it helps at all): [COLOR="Blue"][http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11b.html#Orinoco]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Linux.Wireless.drivers.802.11b.html#Orinoco")[/COLOR]

Absolutely any help would be greatly appreciated, as I feel that I've run into a wall. Thanx in advance!!

---

