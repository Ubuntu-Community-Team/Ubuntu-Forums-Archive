---
title: "Wifi disabled after update?"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by iamlew on 2009-09-06
Running an acer aspire 5730z

Anyways, I've always had wifi problems on my linux installs. I just realized my wifi ALWAYS works when I first install ubuntu(this time is 9.04). I do the update immediately and my wifi stops working. 

I ran sudo lshw -C network 
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 01
       serial: 00:23:4e:12:f9:45
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath9k latency=0 module=ath9k multicast=yes wireless=IEEE 802.11bgn
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: c2:e5:89:f1:69:2b
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes


I tried going through the trouble shooting guide but it kind of sucks because my card is recognized so I go to step 2 and it tells me to check whether it is enabled, disabled, etc then it says for disabled cards go to step one, which is make sure it is turned on.

I even tried booting into windows to make sure the card is enabled (even though my light says it is enabled) and it is.

Any ideas? it uses the atheros drivers I believe (Foxxconn card)

Thanks for any help. If you need more info just let me know what you need. I'm not an expert with linux but I can use terminal and such.

---

