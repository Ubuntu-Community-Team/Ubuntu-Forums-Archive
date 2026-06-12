---
title: "no detecta placa Wifi rtl8723be en Ubuntu 18.04"
date: 2018-12-20
forum: Hardware
---

### Post by manupipo on 2018-12-20
Buenos días, soy nuevo en ubuntu, les comento que no me detecta la placa wifi, estuve siguiendo algunos tutoriales pero no logro hacerlo funcionar, saludos.

```
  *-network                 
       descripción: Ethernet interface
       producto: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:01:00.0
       nombre lógico: enp1s0
       versión: 15
       serie: 3c:52:82:d6:0a:64
       tamaño: 100Mbit/s
       capacidad: 1Gbit/s
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuración: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=10.10.36.220 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       recursos: irq:16 ioport:4000(size=256) memoria:ceb04000-ceb04fff memoria:ceb00000-ceb03fff
  *-network NO RECLAMADO
       descripción: Network controller
       producto: RTL8723BE PCIe Wireless Network Adapter
       fabricante: Realtek Semiconductor Co., Ltd.
       id físico: 0
       información del bus: pci@0000:02:00.0
       versión: 00
       anchura: 64 bits
       reloj: 33MHz
       capacidades: pm msi pciexpress cap_list
       configuración: latency=0
       recursos: ioport:3000(size=256) memoria:cea00000-cea03fff

```

---

