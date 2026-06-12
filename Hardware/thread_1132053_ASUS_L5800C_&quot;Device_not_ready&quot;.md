---
title: "ASUS L5800C &quot;Device not ready&quot;"
date: 2009-04-21
forum: Hardware
---

### Post by magnastik on 2009-04-21
Hi!

since i've updated to 9.04 my wireless card is acting crazy.

The wireless light is always ON (this notebook don't have any switch or shortcut keys to turn ON/OFF wireless card).

But in the Network Applet in the system bar it says "device not ready" and i can't see any wireless networks.

Tried to uninstall/install wireless network card driver, but no lucky.

Any help?

Thanks,
magnastik

---

### Post by calicogeko on 2009-05-06
Same problem. I see there's been no response. Have you solved the problem yet?

---

### Post by Romanian on 2009-05-17
Same problem; bump.

---

### Post by Hilko on 2009-05-29
Me too. Same problem on a Lenovo thinkpad with atheros wireless card.

---

### Post by Kamarada on 2009-07-03
Me Too Toshiba L300

```
mirko@toshi:~$ sudo lshw -C network
[sudo] password for mirko: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:ad:0e:58
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.0.0.3 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:d2:3e:dd:9a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 00:76:62:6e:65:74
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

---

### Post by rimunroe on 2009-09-18
I also have a Lenovo laptop (SL500 with an Atheros ar242x card) and I just had the same problem pop up after hibernating my computer this morning.  Up until now I've had no problems making connections to networks, but ever since waking up from hibernation my computer cannot see any wireless networks. If I click on the network manager applet icon the way I would if I wanted to see the list of wireless networks, it just says "device not ready" under "Wireless Networks".

I experienced another bug which may or may not be related: [http://ubuntuforums.org/showthread.php?t=126878]("http://ubuntuforums.org/showthread.php?t=1268780")
[I]
Edit[/I]
I fixed this problem by adding the lines
```

blacklist ath_pci
blacklist ath_hal

```To the bottom of /etc/modprobe.d/blacklist.conf
(this was all done running 9.04)

---

