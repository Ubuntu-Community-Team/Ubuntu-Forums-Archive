---
title: "D-Link wireless N300 usb adapter dwa 130"
date: 2015-10-21
forum: Hardware
---

### Post by claude1984 on 2015-10-21
How do I get this to work on my PC?

---

### Post by kurt18947 on 2015-10-21
It may be helpful to know what variant of the DWA-130 you have. D-Link seems notorious for releasing different variants of a model using significantly different chipsets. There appear at least B1,C2 and E1 variants of DWA-130.  B1 uses **Ralink** RT2870, C2 and E1 uses **Realtek** RTL8191SU. Info from wikidevi.com. Once you know the chipset, you can research known tricks and workarounds.

---

### Post by ajgreeny on 2015-10-21
If you're not sure of the chipset used show us the output of terminal command ```
sudo lshw -c network
```

---

### Post by claude1984 on 2015-10-21
*-network               
       description: Ethernet interface
       produit: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabriquant: Realtek Semiconductor Co., Ltd.
       identifiant matériel: 0
       information bus: pci@0000:03:00.0
       nom logique: eth0
       version: 09
       numéro de série: bc:ee:7b:dc:d1:cb
       taille: 10Mbit/s
       capacité: 1Gbit/s
       bits: 64 bits
       horloge: 33MHz
       fonctionnalités: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168f-1_0.0.5 06/18/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       ressources: irq:46 portE/S:e000(taille=256) mémoire:d0004000-d0004fff mémoire:d0000000-d0003fff
  *-network
       description: Ethernet interface
       identifiant matériel: 1
       nom logique: usb0
       numéro de série: 02:09:5c:52:65:30
       fonctionnalités: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.206 link=yes multicast=yes

---

### Post by kurt18947 on 2015-10-24
I don't see a wifi adapter listed there, just ethernet. Was the D-Link adapter plugged in when you ran the command?

---

