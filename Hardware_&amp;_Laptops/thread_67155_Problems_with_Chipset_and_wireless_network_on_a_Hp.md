---
title: "Problems with Chipset and wireless network on a Hp pavillino zd 8239"
date: 2005-09-19
forum: Hardware &amp; Laptops
---

### Post by Elius Maximus on 2005-09-19
Hp pavillin zd 8239
CPU: Intel® Pentium® 4-prosessor 630

Systembus: 800 MHz 

Memory: 1024 MB DDR2 533 MHz
Minnetype
	

Diskcontroller: EIDE-HDD, ATA 100
DiskSpeed: 4200 rpm

Nettverksgrensesnitt
	10/100 LAN Ethernet integrert
Wireless tech: 54g™ 802.11b/g WLAN med 125HSM* / SpeedBooster™- og BroadRange™-support

Screen resolution: 1440 x 900
Videocard: ATI MOBILITY RADEON X600-grafikk, 256 MB, Pci Express

Have some slite problems of finding rigth chipset drivers and wireless card drivers to linux. Anyone that has a solution. Have installed the haory ununtu version.

---

### Post by mlomker on 2005-09-19
> Wireless tech: 54g™ 802.11b/g WLAN med 125HSM* / SpeedBooster™- og BroadRange™-support


Not sure if that's a PCI, USB, or a PCMCIA card.

```

lspci
lsusb
cardctl ident

```

One of those should give you the chipset information for your wireless card and that's what you'll need to search for to find a driver.

---

### Post by Elius Maximus on 2005-09-20
Thnx.. appreciate  the help

---

