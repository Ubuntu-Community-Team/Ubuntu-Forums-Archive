---
title: "AR8131 network not detected/disabled?!"
date: 2010-03-06
forum: Hardware
---

### Post by pki on 2010-03-06
Hi.

Tried to install server version 9.04 and 9.10. Both are not detecting the AR8131 network controler. So i plugged in an other network card and installed 9.10.

```
02:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)
```

```
           *-network DISABLED
                description: Ethernet interface
                product: Attansic Technology Corp.
                vendor: Attansic Technology Corp.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth1
                version: c0
                serial: 6c:f0:49:53:aa:3c
                capacity: 1GB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.1-NAPI firmware=N/A latency=0 link=yes multicast=yes port=twisted pair
                resources: irq:17 memory:fdec0000-fdefffff ioport:af00(size=128)

```

---

### Post by IcarusR on 2010-03-06
Is this info with the working (second) card installed or the original "not detected" card installed.

---

### Post by pki on 2010-03-06
The info was of the NOT DETECTED card.

The working i plugged in is showing this:
```
           *-network
                description: Ethernet interface
                product: RTL-8169 Gigabit Ethernet
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:03:01.0
                logical name: eth0
                version: 10
                serial: 00:11:3b:05:55:19
                size: 100MB/s
                capacity: 1GB/s
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.18 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
                resources: irq:19 ioport:de00(size=256) memory:fdbff000-fdbff0ff memory:fdb00000-fdb1ffff(prefetchable)

```

And ifconfig is only showing 'eth0' and 'lo', no eth1.

The mainboard is GA-G31M-E2SL from GIGABYTE with ICH7 chipset. Of course the ethernet is enabled in BIOS.

10.04 Alpha 3 is also not detecting this card in the installer.

---

### Post by IcarusR on 2010-03-06
This webpage might help you...

[http://wonkymind.blogspot.com/2009/10/how-to-get-atheros-ar8131-working-in.html]("http://wonkymind.blogspot.com/2009/10/how-to-get-atheros-ar8131-working-in.html")

---

### Post by pki on 2010-03-06
I already visited this page. The links seems to work but the download is not coming after accepting the licence. Anyone can download it? Not working with FF3.5.x and Opera.

---

