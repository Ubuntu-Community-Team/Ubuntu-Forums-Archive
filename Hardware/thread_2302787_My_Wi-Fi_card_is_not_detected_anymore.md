---
title: "My Wi-Fi card is not detected anymore"
date: 2015-11-13
forum: Hardware
---

### Post by arthurd2 on 2015-11-13
Hi I have a problem I really don't manage to solve actually, I searched already a lot on forums but I didn't found any solutions.

I'm working on Ubuntu 14.04.

Lately my computer didn't detect wifi anymore, I already checked if a button was disable on my keyboard but it's not the case.

Here are some information from the terminal:

> 
   iwconfig  
 eth0              no wireless extensions.  

 

 lo             no wireless extensions.  

 

 sudo lshw -C network 

        *-network                

            description: Ethernet interface  

            produit: NetLink BCM57785 Gigabit Ethernet PCIe  

            fabriquant: Broadcom Corporation  

            identifiant matériel: 0  

            information bus: pci@0000:02:00.0  

            nom logique: eth0  

            version: 10  

            numéro de série: b8:88:e3:41:5a:c1  

            capacité: 1Gbit/s  

            bits: 64 bits 

            horloge: 33MHz  

            fonctionnalités: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation  

            configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.134 firmware=sb latency=0 link=no multicast=yes port=twisted pair  

            ressources: irq:16 mémoire:c0430000-c043ffff mémoire:c0440000-c044ffff mémoire:c0450000-c04507ff  

       *-network NON-RÉCLAMÉ  

            description: Network controller  

     produit: BCM4313 802.11bgn Wireless Network Adapter  

            fabriquant: Broadcom Corporation  

            identifiant matériel: 0  

            information bus: pci@0000:03:00.0  

            version: 01  

            bits: 64 bits 

            horloge: 33MHz  

            fonctionnalités: pm msi pciexpress bus_master cap_list  

            configuration: latency=0  

            ressources: mémoire:c0500000-c0503fff  

 


for me it seems like the wifi card doesn't exist anymore for my computer...

Thanks for your help ;-)

---

